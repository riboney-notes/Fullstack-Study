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

## CH3 Designing a programming interface

## Main Concepts
- Transforming API goals into a API
- Identifying and mapping REST resources and actions
- Designing API data from concepts
- Differentiating between REST APIs and REST architectural style
- Why REST architectural style matters for API design

### 3.1 Introducting REST APIs

- API requests:
  - HTTP method - indicates what the consumber wants to do with the resource (GET, POST, etc)
  - path - address identifying a resource on the server

- API responses:
  - HTTP status code - tells how the request processing went (200:Ok, etc)
  - Response body - contains the content of the resource identified by the path in the request (json data)

- HTTP
  - protocol that allows exchange of documents (resources) between applications over the internet
  - used by many applications, like web browsers and webservers that communicate via HTTP

- Resources
  - HTML pages
  - CSS files
  - Javascript files
  - images
  - JSON
  - etc

- REST API
  - allows consumers to manipulate resources identified by paths using HTTP methods

### 3.2 Transposing API goals into REST API

- Collection
  - resource that contains other resources of the same type

- Path parameters
  - some ID or paramter in the path that uniquely identifies a resource

- Resource path design
  -  `/{plural name of item}/{item id}`

- Search query path example
  - GET /example?param1=value1&param2=value2
  - GET /products?free-query=something

- HTTP methods overview
  - POST
    - Action: create or add new resource
    - Parameters: request body
  - GET
    - Action: Read, retrieve, search
    - Parameters: URL query params
  - PATCH
    - Action: Modify, partially update
    - Parameters: request body
  - PUT
    - Action: replace or create if not existing
    - Parameters: request body
  - DELETE
    - Action: remove, delete
    - Parameters: URL query params
