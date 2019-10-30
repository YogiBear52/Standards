# Performance

IO is slow. Especially networking which is the slowest operation is software development.

On demand request should usually take some ms. (50-250). User is waiting. There are tons of articles about users abandoning the site because it is slow.

## Compression

- deflate, Gzip, Brotli
- Brotli is the new trending with highest result compression. Use it.
- As a service, make sure to compress by the client capabilities (Accept Encoding: df,gzip,br)
- What about compressing between B-B ?
  - If latency is really low, there is not need of this CPU overhead.
- Give the ApiGateway/LoadBalancer the job to compress - They are good at it
- Don't compress if the data is lower than X size. (Most libraries will do it automatically)

## Http/2

- Use [Http/2](Protocols/Http.md) for it's improvement in low latency

## Server Physical Location

Far distance between server and client might cause a high latency.
For example between Europe to Israel, avg latency is about 65 ms. between USA to Israel, the AVG latency is about 220 ms.

- Consider using a local server for you clients.
  - Use a Geography based DNS to route your clients to the closest server

## UDP vs TCP

- When data hermeticity is not important for us, UDP is way faster.

## Pagination

- Some requests might carry large amount of payload
- We should con
