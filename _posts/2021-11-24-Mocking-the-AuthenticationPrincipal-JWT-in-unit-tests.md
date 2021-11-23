---
published: false
---
Often it is needed to write tests for our application that deal with some form of Authentication, and, even more frequently, the goal of these tests is **not** to worry about the actual authentication mechanism itself, but, instead, of what logic occurs when we _assume_ that the authentication was successful. In testing jargon, we want to simply unit test the logic that sits _behind_ the authentication mechanism, not concerning ourselves with the authentication piece itself.

A somewhat common pattern for writing resource and/or controller classes when dealing with Authentication is to leverage one of the many annotations of Springboot, hoping that it does its magic, and, most certainly, it does:

The `@AuthenticationPrincipal` annotation can be applied to a method parameter to get us the value at runtime of whatever authentication method we are using that implements the `Principal` interface. We will focus ourselves on using a JWT as an authentication principal and we will see how we can mock it in the context of a _unit_ test and not of an _integration_ test. That was covered before, right [here](https://bruno-oliveira.github.io/techblog/Mocking-Authorization-principal-in-a-Springboot-integration-test/). While there is value in being able to setup a complete `MockMvc` instance using the `WebApplicationContext webApplicationContext`, that is a level of testing that goes one step further than simple unit tests, and, not only with authentication, but, with everything else, it's desirable for assessing extra correctness to have both levels of testing in place.

However, in order to use a mock JWT in the context of a unit test, we will see that it requires us to have a deeper understanding of how Spring Security works and also an understanding of how we can make our `MockMvc` instance correctly wire up the JWT token from a `standaloneSetup`. But, firstly, we can attempt to write a standard unit test and see what result we get, so, we can dig deeper into how we can solve our problem. 

A standard unit test using the `MockitoExtension` and configuring our `mockMvc` instance with the standalone setup could look like this:

```java
//some java
```

However, if we try to run this test, we see the following error, which, at a first glance, feels non-obvious:


```bash
//error
```

What this tells us is that the test context can't resolve the JWT, even though we are passing the token as expected. So, what is happening here exactly? Well, the important thing to understand is that we are passing our `AuthenticationPrincipal` to our controller method via a method annotation and the way Springboot deals with method annotations is by leveraging the work done by a class of the type 
