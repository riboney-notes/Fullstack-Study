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
    - Usage would consist of `date` and `count` numbers
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
- 
## Health check route

- some base URL to check if server is running
