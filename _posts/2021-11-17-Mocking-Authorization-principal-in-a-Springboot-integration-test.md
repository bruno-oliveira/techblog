---
published: false
---
### Introduction

Most web applications require a certain type of tests to ensure its correctness: we need unit tests, integration tests and we can even have acceptance tests as well.

Usually, integration tests are particularly challenging to write because they exercise several pieces of the application all together and a lot of context needs to be first set up, in order to actually write a proper integration test.

This post will cover a short example showcasing how to write a test in Springboot that actually allows to test for the presence of a JWT token in a request header for an app that needs it to complete a specific request.

### A brief introduction to MockMvc

MockMvc is the main entry point for server-side Spring MVC test support, and, in essence, it allows one to configure a complete test context application so that it can be used for testing. Usually, for a given test class, it's configured in a `setUp` method as follows:

```java
@Autowired
private MockMvc mockMvc;

 @BeforeEach
    void setUp(WebApplicationContext webApplicationContext, RestDocumentationContextProvider restDocumentation) {
        this.mockMvc = MockMvcBuilders.webAppContextSetup(webApplicationContext)
            .apply(documentationConfiguration(restDocumentation))
            .apply(springSecurity())
            .build();
    }
```

Using the builder pattern, we can create a prepared instance of `MockMvc` that has support for adding documentation and, more importantly, support for Spring Security, meaning that we can test endpoints that are secured from within our tests.

### Using the annotation `@AuthorizationPrincipal` in an endpoint to require authorization

From within a resource class, we can pass a `JWT` token for example, to be passed in the header of a request as follows:

```java
@GetMapping(value = {"/someEndpoint"})
    public ResponseEntity<?> getData(@AuthenticationPrincipal Jwt jwtToken){
           String name = jwtToken.getClaimAsString("name");
           SomeDTO response = process(name);
           // do some processing.....

           return ok(response);
}
```

Note that we simply inject the annotation directly behind of the JWT parameter in the method header, and like that we have access to the JWT constituent parts in the method itself.

This annotation, essentially, is used to resolve `Authentication.getPrincipal()` to a method argument.

Let's see how to actually test the endpoint with a mock JWT.

### Testing the endpoint with a mock JWT

In order to make an authorized request on a resource server, you need a bearer token. If your resource server is configured for JWTs, then this would mean that the bearer token needs to be signed and then encoded according to the JWT specification. All of this can be quite daunting, especially when this isn’t the focus of your test.

Fortunately, there are a number of simple ways that you can overcome this difficulty and allow your tests to focus on authorization and not on representing bearer tokens. We’ll look at two of them now:

- Using a jwt() RequestPostProcessor


The first way is via a RequestPostProcessor. The simplest of these would look something like this:

```java
mvc
    .perform(get("/endpoint").with(jwt()));
```

What this will do is create a mock Jwt, passing it correctly through any authentication APIs so that it’s available for your authorization mechanisms to verify.

By default, the JWT that it creates has the following characteristics:

```json
{
  "headers" : { "alg" : "none" },
  "claims" : {
    "sub" : "user",
    "scope" : "read"
  }
}
```

And the resulting Jwt, were it tested, would pass in the following way:

```java
assertThat(jwt.getTokenValue()).isEqualTo("token");
assertThat(jwt.getHeaders().get("alg")).isEqualTo("none");
assertThat(jwt.getSubject()).isEqualTo("sub");
GrantedAuthority authority = jwt.getAuthorities().iterator().next();
assertThat(authority.getAuthority()).isEqualTo("read");
```

These values can, of course be configured.

Any headers or claims can be configured with their corresponding methods:

```java
mvc
    .perform(get("/endpoint")
        .with(jwt().jwt(jwt -> jwt.header("kid", "one").claim("iss", "https://idp.example.org"))));
mvc
    .perform(get("/endpoint")
        .with(jwt().jwt(jwt -> jwt.claims(claims -> claims.remove("scope")))));
```

The scope and scp claims are processed the same way here as they are in a normal bearer token request. However, this can be overridden simply by providing the list of GrantedAuthority instances that you need for your test:

```java
mvc
    .perform(get("/endpoint")
        .with(jwt().authorities(new SimpleGrantedAuthority("SCOPE_messages"))));
```

Or, if you have a custom Jwt to Collection<GrantedAuthority> converter, you can also use that to derive the authorities:


```java
  mvc
    .perform(get("/endpoint")
        .with(jwt().authorities(new MyConverter())));
```
  
You can also specify a complete Jwt, for which Jwt.Builder comes quite handy:

  
```java
Jwt jwt = Jwt.withTokenValue("token")
    .header("alg", "none")
    .claim("sub", "user")
    .claim("scope", "read");

mvc
    .perform(get("/endpoint")
        .with(jwt().jwt(jwt)));
  ```


-Using authentication() RequestPostProcessor

The second way is by using the authentication() RequestPostProcessor. Essentially, you can instantiate your own JwtAuthenticationToken and provide it in your test, like so:

```java
Jwt jwt = Jwt.withTokenValue("token")
    .header("alg", "none")
    .claim("sub", "user")
    .build();
Collection<GrantedAuthority> authorities = AuthorityUtils.createAuthorityList("SCOPE_read");
JwtAuthenticationToken token = new JwtAuthenticationToken(jwt, authorities);

mvc
    .perform(get("/endpoint")
        .with(authentication(token)));
```

Note that as an alternative to these, you can also mock the JwtDecoder bean itself with a @MockBean annotation.
