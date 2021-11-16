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
@GetMapping(value = {"/someEndpoint})
    public ResponseEntity<?> getData(@AuthenticationPrincipal Jwt jwtToken){
           String name = jwtToken.getClaimAsString("name");
           SomeDTO response = process(name);
           // do some processing.....

           return ok(response);
}
```
