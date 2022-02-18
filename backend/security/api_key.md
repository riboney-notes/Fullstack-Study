# API Security

## Express API key

### Materials

- [How the Heck Do API Keys Work? - Griffith](https://www.youtube.com/watch?v=cF_MCAmuoI4)

### Notes

- Registering for API key
  - Send email from form to `api/register` endpoint with POST
  - send 201 status upon sucess
- API key middleware
  - all validation is done here
- API key, email, host of registerer, etc are saved into memroy
  - along with usage and ID
    - Usage would be an array consisting of  objects that contain `date` and `count` numbers
  - Host
    - When getting API key and using it for client application...anyone using the application can potentially access the token
    - That is why in the server, the host (domain) is associated with the key and requests have the API key checked with the saved host information to see if they match and prevent others from using your API key and abusing it
  - If request comes from developer endpoint, then check if request headers match API key and host
    - Increment usage 
    - Check usage against API_MAX usage constant
- Response sent back from server
  - Check response body for error messages
  - Save API key in session storage
    - Could also save API token thats returned in the code instead of sessions
- Sending key to server
  - Send key through query string
    - Ex: http://localhost:4000/example?api_key=asdfdfjojo23431
  - Send key through URL or endpoint
    - Ex: http://localhost:4000/example/asdfdfjojo23431
  - Send through headers
    - Ex: ("x-api-key, "asdfdfjojo23431")
- APIkey middleware
  - genKey() to generate API key
  - createUser() to register a user
    - Get todays date and populate new user fields such as: api_key from genKey(), email from req, host from req, and usage consisting of todays date and count initalizaed to 0 
  - validateKey() to use to check for API_key for endpoints that require API key 
    - you attach this middleware directly in the router functions that require it (so router.get(/endpoint, validateKey, (req, res) =>....))
    - everytime validateKey is run, usage is incremented
    - the host and api_key values are provided by `req`: `req.headers.origin` for host and 
    - the host and api_key is used to search for user; if user found then api key is valid..if not found then reject 
    - Get todays date; find the object in usage where todaysDate matches the date in usage, and get the index of that object in the usage array
      - Then use index to check the count of that object and see if it is GTE. API_REQUESTS max; if GTE, then send back error response with HTTP status 429; if not, then incremenet count and call next() to go back to the middleware pipeline and run the rest of the code
## Health check route

- some base URL to check if server is running
