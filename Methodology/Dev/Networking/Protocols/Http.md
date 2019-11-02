# Http

Old protocol.

- Use the highest http version
  - Http/2 > Http 1.1 > http 1.0
  - Http/2
    - Data compression of HTTP headers
    - HTTP/2 Server Push
    - Multiplexing multiple requests over a single TCP connection
- Don't make raw HTML requests. Use one of the [conventions](Conventions/REST.md) REST/GraphQL

## HTTPs (Secure Http)

- Frontend to Backend - Must
- Backend to Backend - Not a must, consider.

### Motivation

- Secure (F-B)
  - Man in the middle
- Allows Http/2
- Slower than Http ?
- Google AMP
- Google AMP (Accelerated Mobile Pages)

### Best Practices

- Make sure you server is using latest version of TLS libraries - for security and performance reasons
- Monitor certificate
- Generate a certificate with a wildcard of \*.Bob.com, so it will support all sub domains
- Redirect all http traffic to HTTPs
  - Usually done by the ApiGateway
