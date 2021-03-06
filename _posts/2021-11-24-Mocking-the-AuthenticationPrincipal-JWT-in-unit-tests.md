---
layout: post
title: Mocking the JWT AuthenticationPrincipal in the context of unit tests
published: true
---  
Often it is needed to write tests for our application that deal with some form of Authentication, and, even more frequently, the goal of these tests is **not** to worry about the actual authentication mechanism itself, but, instead, of what logic occurs when we _assume_ that the authentication was successful. In testing jargon, we want to simply unit test the logic that sits _behind_ the authentication mechanism, not concerning ourselves with the authentication piece itself.

A somewhat common pattern for writing resource and/or controller classes when dealing with Authentication is to leverage one of the many annotations of Springboot, hoping that it does its magic, and, most certainly, it does:

The `@AuthenticationPrincipal` annotation can be applied to a method parameter to get us the value at runtime of whatever authentication method we are using that implements the `Principal` interface. We will focus ourselves on using a JWT as an authentication principal and we will see how we can mock it in the context of a _unit_ test and not of an _integration_ test. That was covered before, right [here](https://bruno-oliveira.github.io/techblog/Mocking-Authorization-principal-in-a-Springboot-integration-test/). While there is value in being able to setup a complete `MockMvc` instance using the `WebApplicationContext webApplicationContext`, that is a level of testing that goes one step further than simple unit tests, and, not only with authentication, but, with everything else, it's desirable for assessing extra correctness to have both levels of testing in place.

However, in order to use a mock JWT in the context of a unit test, we will see that it requires us to have a deeper understanding of how Spring Security works and also an understanding of how we can make our `MockMvc` instance correctly wire up the JWT token from a `standaloneSetup`. But, firstly, we can attempt to write a standard unit test and see what result we get, so, we can dig deeper into how we can solve our problem. 

A standard unit test using the `MockitoExtension` and configuring our `mockMvc` instance with the standalone setup could look like this:

```java
@DisplayNameGeneration(DisplayNameGenerator.ReplaceUnderscores.class)
@ExtendWith(MockitoExtension.class)
class SomeResourceTest {

    private MockMvc mockMvc;

    private SomeResource someResource;

    @Mock
    private SomeService someService;

    @BeforeEach
    void setUp() {
        someResource = new SomeResource(someService);
        mockMvc = MockMvcBuilders.standaloneSetup(someResource)
                .build();
    }
    
    @Test
    void get_correct_result_when_token_is_used() throws Exception {
        var data = new HashSet<String>();
        data.add("data1");

        when(someService.getData(any())).thenReturn(new ResultDTO(data));

        mockMvc.perform(get("/data")
                .contentType("application/json")
                .with(jwt().jwt(builder -> builder.tokenValue("value").claim("data", "data1").header("Authorization", "Bearer value"))))
            .andExpect(status().isOk());
    }
    

```

However, if we try to run this test, we see the following error, which, at a first glance, feels non-obvious:


```bash
org.springframework.web.util.NestedServletException: Request processing failed; nested exception is org.springframework.beans.BeanInstantiationException: Failed to instantiate [org.springframework.security.oauth2.jwt.Jwt]: Constructor threw exception; nested exception is java.lang.IllegalArgumentException: tokenValue cannot be empty

	at org.springframework.web.servlet.FrameworkServlet.processRequest(FrameworkServlet.java:1014)
	at org.springframework.web.servlet.FrameworkServlet.doGet(FrameworkServlet.java:898)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:645)
	at org.springframework.web.servlet.FrameworkServlet.service(FrameworkServlet.java:883)
	at org.springframework.test.web.servlet.TestDispatcherServlet.service(TestDispatcherServlet.java:72)
	at javax.servlet.http.HttpServlet.service(HttpServlet.java:750)
	at org.springframework.mock.web.MockFilterChain$ServletFilterProxy.doFilter(MockFilterChain.java:167)
	at org.springframework.mock.web.MockFilterChain.doFilter(MockFilterChain.java:134)
	at org.springframework.test.web.servlet.MockMvc.perform(MockMvc.java:183)
```

What this tells us is that the test context can't resolve the JWT, even though we are passing the token as expected. So, what is happening here exactly? Well, the important thing to understand is that we are passing our `AuthenticationPrincipal` to our controller method via a method annotation and the way Springboot deals with method annotations is by leveraging the work done by classes implementing the `HandlerMethodArgumentResolver` interface and then wiring it to our `MockMvc` class as follows:

```java
MockMvc mockMvc = MockMvcBuilders
                .standaloneSetup(new SomeTestController())
                .setCustomArgumentResolvers(new CustomArgumentResolver())
                .build();
```

Let's look at our controller class:

```java
@GetMapping
    public ResponseEntity<?> getDataResults(@AuthenticationPrincipal Jwt principal) {
        List<String> data = principal.getClaimAsStringList("data");
        var responseDTO = someService.fetchData(principal);
        return data.isEmpty() ? noContent().build() : responseDTO;
    }
```

We see that we pass our JWT to our method with: `@AuthenticationPrincipal Jwt principal` 
This is the critical piece of our method that we will need to link with our `CustomArgumentResolver`:

```java
public class CustomArgumentResolver implements HandlerMethodArgumentResolver {
    @Override
    public boolean supportsParameter(MethodParameter parameter) {
        return parameter.getParameterType().isAssignableFrom(Jwt.class);
    }
    @Override
    public Object resolveArgument(MethodParameter parameter, ModelAndViewContainer mavContainer,
                                  NativeWebRequest webRequest, WebDataBinderFactory binderFactory) {
      var jwtToken = JwtBuilder.value(...).header(..).claims(...).build();
        var jwt = new Jwt(jwtToken);
        return jwt;
    } 
 } 
```

Note how we define the class from which our method parameter is assignable from as being exactly the type of the class that matches the implementation of the annonation in our controller class, which, in our case, is `Jwt`.

Now, with all this wiring in place, we can re-run our test, and verify that it will pass!

We then see the flexibility that we can gain by delving deep into how `MockMvc` can be configured and how we can write better tests at all levels of responsibility when needing to work with `Authentication` related classes in our code.
