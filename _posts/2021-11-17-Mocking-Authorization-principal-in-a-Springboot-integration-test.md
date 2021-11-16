---
published: false
---
### Introduction

Most web applications require a certain type of tests to ensure its correctness: we need unit tests, integration tests and we can even have acceptance tests as well.

Usually, integration tests are particularly challenging to write because they exercise several pieces of the application all together and a lot of context needs to be first set up, in order to actually write a proper integration test.

This post will cover a short example showcasing how to write a test in Springboot that actually allows to test for the presence of a JWT token in a request header for an app that needs it to complete a specific request.

### A brief introduction to MockMVC


