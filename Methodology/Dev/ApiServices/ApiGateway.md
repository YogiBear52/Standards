# ApiGateway

## Motivation

- Helps client to access different services in a micro-services architecture
- Used as a contract between the clients and us
  - [SLA](../ApiService/SLA.md) will be apply on this ApiGateway
- Organize all available public APIs in one place
- Security -> One external endpoint which is public to the evil world - only one endpoint to protect.
- Encapsulates many api services cross concerns - Authentication, Authorization, Caching, TLS, Retry policies (continue reading for more details)
- No need of ApiGateway when you have minimal set of services - overhead.
- ApiGateway will increase complexity of overall architecture and will be another point of failure

## How

- One ApiGateway per contract / system / product
- In many cases, ApiGateway product is also a LoadBalancer. No need to manage two tools.
- Authentication and Authorization
  - The ApiGateway will ensure all traffic goes through it is authenticated and authorized if needed.
  - The ApiGateway will route the traffic first to authentication service, then to the services (Or will drop the traffic)
  - This way, all services are dismissed from most of implementing it
- Integrate APiGateway with dynamic service discovery
  - Do not HardCode you services IP
  - Service Discovery approach - Each service will notify and register in the ApiGateway pool if alive.(Link to Service Discovery subject)
- (Controversial Best Practice) - Make the ApiGateway to retry polices
- Simple Caching
- Compression traffic
- CORS handling (?? Research more)
- TLS
  - The ApiGateway will hold the DNS certificate and encrypt and decrypt all traffic
  - Clients will contact it with SSL and it will pass a non encrypted traffic to it's services
    - This way we don't have to worry about installing certificates on each service
    - This machine is utilized to encrypt and decrypt very fast - more than your services.
- Metrics collection
  - Send all ApiGateway traffic logs to your logging system. These logs will help you see the big picture.

## High availability

How do we make an ApiGateway, which is the last step before reaching the client ?

- Multiple records in the DNS
- Floating IP (Link to floating IP subject)
