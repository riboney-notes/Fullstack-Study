# HTTP

## Internet

<details>
    <summary>What happens when you enter a URL into address bar of webbrowser? Discuss the server, clients, and communication process</summary>

    * A webserver supplies the client (your webbrowser) with a collection of files (CSS, HTML, JS, resources, etc) by an application protocol called HTTP
</details>

<details>
    <summary>What is a protocol?</summary>

    * A message format/ agreement/ contract of how machines (server and client) communicate with each other
    * Client makes a request to the server and then waits for the server's response (and vice-versa)
</details>

<details>
    <summary>What are IP address and port numbers</summary>

    * IP Address
      - Unique label for a device used to identify that device on the internet
      - Kinda like a internet "phone-number"
      - Enables messages to go to and from specific devices
      - Ex: `192.168.0.1`
    * Port numbers
      - Allows targeting of specific services/ applications within devices
      - Allows computers to differentiate between different kinds of traffic (ex: port 80 is usually reserved for HTTP messages)
      - Ex: `192.168.0.1:1234`
      - there can be thousands of ports for a singular device/ IP address
</details>

<details>
    <summary>What is DNS</summary>

    * Domain Name System (DNS) is a distributed database that translates domain names (ex: `www.google.com`) to an IP address
    * Keeps track of domain names and their corresponding IP addresses on the Internet
    * DNS databases are stored on DNS servers
      - there is a world-wide network of hierarchically organized DNS servers which handles requests for resolving domain names to IP addresses
    * DNS process:
      1. Send HTTP request for a domain name (ex: www.google.com)
      2. Check local DNS cache for the IP address for the domain name, if available
      3. If not found in cache, send DNS request to the DNS server to obtain IP address for the domain
      4. HTTP request is then directed to the web server matching the IP address
      5. Webserver accepts request and sends response back to browser
      6. Browser displays the webpage you requested (google)
</details>

## HTTP Protocol

<details>
    <summary>Describe how HTTP is stateless</summary>

    * Stateless protocols are designed in such a way that each request/response pair is completely independent of the previous one
    * This means that the server need not save information/ state between HTTP requests
    * Pros: 
      - Server does not need to clean up any state leftover from previous HTTP requests
      - Server does not need to utilize its memory for persistenting state information
    * Cons:
      - Its harder to develop stateful applications
        - Ex: When going on Facebook and logging in, that is one request/ response cycle. When you click on any FB links (pictures, comments, etc), that initiates another request/ response cycle; Since HTTP is stateless, how does the facebook application remmeber that you are logged in? And that the request is coming from you? (vs any other user...especially for private pages/ data)? 
</details>

// TO-DO: 
  - HTTP requests
  - HTTP Responses
  - Stateful Web apps
  - Security
  
## URL

* For `http://www.example.com:88/home?item=book`:
  - `http`
    - Scheme that tells client how to access the resource
    - in this case, its to use the HTTP protocal to make a request
    - in other URLs, it could be `ftp`, `mailto`, `git`, etc
  - `www.example.com`
    - Host that tells client where the resource is hosted or located
  - `88`
    - Port or port number that is only required if you use a port other than the default (`80` for HTTP and `443` for HTTPS)
  - `/home`
    - Path that shows what local resource is requested
  - `?item=book`
    - Query string made up query parameters that is used to send data to server
    - `?` marks start of query string
    - `&` used when adding more parameters to the query string

* Url Encoding
  - URLs only accept certain characters in the ASCII set
  - Other characters (as well as reservered characters) have to be encoded
    - Encoding works by replacing non-URL-valid charaters with `%` followed by 2 hexadecimal digits that represent ASCII code of the character

## Stateful Webapps
* HTTP protocol is stateless
  - Therefore server does not hang on to information between each request/response cycle
* Every request or response is treated as a brand new entity that are not aware of each other
* However, even though stateless, we can stay logged into most websites....even though response/request should not be aware that we are logged in
  - How is our login state being persisted? How does the server know to remember your username and display it after sending new request?

## Sessions
* Where server sends unique token (session identifier/ session id) to client
  - whenever client makes a request to that server, the client appends this token as part of the request it sends
  - this allows the server to identify clients
* Each request is still stateless; its just that a session id is being passed back and forth to help server identify client
* Server needs to handle session expiration and session data storage
* Process
  - Every request must be inspected to see if it contains a session id
  - If session id is found, server must check to verify its valid
  - Once verifed, server needs to retrieve session data that is based on session id
  - Then, server needs to combine session data with the HTML to send back as a response
    - This can be very expensive since page needs to be recreated with all the data for every request you send (i.e clicking like or refreshing page or etc)
      - Some sites get away with this by using ajax and other advanced techniques
* Session data is stored somewhere in the server and the session id is stored on the client
  - the session id acts as a `key` to the session data `value` stored server side
* Cookies
  - piece of data sent from server and stored in client during request/response cycle
  - they are small files stored in the browser and contain session information
  - Cookies are compared with the session data on each request to identify the current session
    -- often when you log out, cookies are erased, and the process has to start again/ you dont see your session data

## Ajax
* Stands for async javascript and XML
* Allows browsers to handle request/response without a full page refresh
  - This means that when you click on a "like" button....the page doesn't refresh...ajax asyncronously handles requests and responses and updates the HTML with the results (normally with callbacks)

## Security
* In HTTP, request/response data is sent as strings
  - so any attacker can do packet sniffing techniques to read the messages sent back and forth
  - they can copy session id and craft a request to the server and falsely pose as the client
    - Thereby being logged in without needing username or password

* With HTTPS, every request/ response is encrypted before being transported on the network
  - So packet sniffing is useless unless they can decrypt somehow
  - Messages are sent through cryptographic protocol called TLS for encryption
    - Earlier versions of HTTPS used SSL until TLS
    - These protocols use certificates to communicate with remote servers and exchange security keys before data encryption happens (need more info)

* Same-origin policy
  - policy unrestricted interaction between resources originating from the same origin, but restricts certain interactions between resources originating from diff. origins
  - Origin - combination of url's scheme, hostname, and port
  ```
  http://mysite.com/doc1 would be considered to have the same origin as http://mysite.com/doc2, but a different origin to https://mysite.com/doc2 (different scheme), http://mysite.com:4000/doc2 (different port), and http://anothersite.com/doc2 (different host).
  ```
  - Allowed:
    - Linking, redirects, or form submissions to different origins are allowed
    - Embedding of resources from other origins, such as scripts, css stylesheets, images, and other media, fonts, and iframes
  - What are restricted are cross-origin requests where resources are being accessed programmatically using APIs such as `XMLHTTPRequest` or `Fetch`
  - CORS (cross-origin resource) is the mechanism that allows servers to server resources cross-origin to certain specified origins
  - Protects against session hijacking and other serves for other security stuff

* Session hijacking
  - this is where attacker gets a hold of session id without even knowing user's password or username
  - countermeasures
    - Resetting sessions; this is where client is required to re-login or authenticate which causes session id to change, rendering the one attacker might have, useless
      - usually done before purchases or deleting accounts
    - Setting expiration time on sessions
    - Use HTTPS to minimize chance of attacker getting session ID

* Cross-Site Scripting (XSS)
  - Happens when you allow users to input HTML or JS that ends up being executed by the site directly
    - Caused by not sanitizing input
  - Basically means users can input code into form data that would get exectuted by server or browser
  - Prevent it by sanitizing or escaping input
