# Rest Standards

## Syntax

- Resources - /getAllProducts --> /products
- Parameters - /getProductByName --> /products?name='ABC'
- Resources name will always be plural

## Methods

- Get - Get a resource or a collection of resources
- Post - Creates a resource or a collection of resource
  - Return 'Location' header with the value of the new resource
- Put - Updates the whole resource
- Path - Updated the diff between given and existing resource
- Delete - Delete and existing resources

## Http Status codes

### 200.x

- 200 OK
- 201 Created + location header
- 202 - Accepted (In process)
- 204 No-Content (for example PUT of the same resource)

### 300.x

- 304 Not Modified (Caching Etag)
- Redirects

  - Make sure to send the URL of the ApiGateway and not of the specific server processed the request.

### 400.x

User related errors. "The user has used the API in a wrong way".

- 400 Bad Request
- 401 Unauthorized, 403 Forbidden
- 404 - Not Found

## General BP

- REST suppose to be stateless
  - Don't implement a session tracking ID on top of REST requests.
- URL in Rest is considered to be the ID of the Resource
  - Treat it as a holly URL and never change it.
  - Use versioning (api/v1/...
    - (Research more) - header vs url
- Pagination in case returning a lot of data
  - /products?limit=25&offset=50
  - Pagination is not easy to implement in complex data.
- Errors - RFC 7807 - Problem Details
- Documentation - OpenApi spec
