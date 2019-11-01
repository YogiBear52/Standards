# Service

## Controllers and Actions

- Validate input from request
- Check Authorization for a specific resource
  - General Authorization and Authentication check should be globally configured
- Call the logic module
  - Controller will never contain logic
  - We must decouple the Sever Platform(Controller) from the logic
- Return appropriate [HTTP response](../Networking/Protocols/Http.md)

## Common Middlewares

- Routing
- CORS (External handling is preferred)
- Compression (External handling is preferred)
- Authentication validation + processing
  - Implementation of the whole Authentication flow should be as an external service. The ApiGateway have to handle it and route only authenticated request to the service.[ApiGateway](ApiGateway.md)
- General service Authorization (External handling is preferred)
- Request logger (One log to each request-response)
- Error handler
