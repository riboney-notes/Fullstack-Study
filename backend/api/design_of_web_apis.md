# The Design of Web APIs

[*link to book*](https://www.manning.com/books/the-design-of-web-apis)

## CH1 What is API design?

### Main Concepts
- What an API is
- Why API design matters
- What designing an API means

### 1.1.1 Web API is a web interace for software

- API allows communcation and interaction between separate things
- There is a provider of the API that exposes the API to consumers who uses the API
- Communication & interaction is done VIA the internet and HTTP protocol

### Summary
- Web APIs turn software into reusable bricks that can be used over a network with the HTTP protocol.
- APIs are interfaces for developers who build the applications consuming them.
- API design matters for all APIs—public or private.
- Poorly designed APIs can be underused, misused, or not used at all, and even unsecure.
- Designing a good API requires that you take the whole context of the application into consideration, not only the interface itself.

## CH2 Designing an API for its users

### Main Concepts
- Which perspective to focus on when designing APIs
- Approaching API design like designing a user interface
- How to accurately determine an API's real goals

### Summary
- To be easy for consumers to understand and use, an API must be designed from the consumer's perspective
- Designing an API from the provider's perspective by bluntly exposing inner workings (data, code, logic, etc) inevitably leads to hard to understand and hard to use APIs
- API goals list is good foudnation for an API
- Identifying the who, what, why, and how is key to building a good API goals list
