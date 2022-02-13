# NodeJS Ecosystem

*This document gives an overview of the design patterns, tools, libraries, and common practices for developing backends with NodeJs

## Overview

![Express API Architecture](https://www.coreycleary.me/_next/static/media/Express-REST-API-Struc.aa7ecaa0c41dbb7344c70665a5f5e259.png)
![Express API Architecture 2](https://www.section.io/engineering-education/express/express.png)

**Technical Details**

<details>
  
  <summary>HTTP Request comes from clients (ex: Website, android app, etc)</summary>
  
   - See [link](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) for what HTTP requests do
</details>

<details>
  <summary>HTTP Requests are processed by the Express app</summary>
  
   ![Diagram Flow of Request](https://miro.medium.com/max/642/1*kMNzu4zx40QvwQUWa9dCOw.png)
   - The contents of the HTTP request are encapsulated in Express `req` object, along with other details
      - See [API](https://expressjs.com/en/api.html#req) for details concerning the `req` object 
   - The `req` object is passed through a series of *middleware* functions
      - see [link](https://dzone.com/articles/understanding-middleware-pattern-in-expressjs) for some details on what middleware does and looks like
</details>

<details>
  <summary>HTTP Response is formed by the Express app and sent to client</summary>
  
  *This section will assume that the Express app is following the [3-Layer Architecture](https://bytearcher.com/articles/node-project-structure/) ... [another link](https://www.codementor.io/@evanbechtol/node-service-oriented-architecture-12vjt9zs9i)*
  - The router function is responsible for initiating the core logic of the Express app
  - Router invokes the appropriate `controller` function, passing the [`req`](https://expressjs.com/en/api.html#req) and [`res`](https://expressjs.com/en/api.html#res) objects
  - The controller functions invoke the appropriate `service` function, passing the payload (i.e. data) from `req`
  
  <details>
  <summary>The service functions acts upon the payload and applies the business logic (validation, actions, rules, etc)</summary>
    
  - the service function also interacts with the `data` functions or 3rd party services to retrieve data
  - the service function's main goal is forming a response to the client's HTTP request, which is sent to the calling controller function
  - The controller function takes the response from the service layer, and uses the `res` object to encapsulate it in a HTTP response object to send back to the client
   </details> 
    
</details>
