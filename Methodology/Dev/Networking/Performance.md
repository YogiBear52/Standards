# Performance

IO is slow. Especially networking which is the slowest operation is software development.

On-Demand requests should usually last less than half a second. (50-250). User is waiting.

- There are tons of articles about users abandoning the site because it is slow.

## Compression

- Deflate, Gzip, Brotli Algorithms
- Brotli is the new trending algorithm by Google, calming for the best compression ratio and speed.
- As a service, make sure to compress by the client capabilities (Accept Encoding: df,gzip,br)
- What about compressing between B-B ?
  - If latency is really low, there is not need of this CPU overhead.
- Give the ApiGateway/LoadBalancer the job to compress - They are good at it
- Don't compress if the data is lower than X size. (Most libraries will do it automatically)
- Response in Json format, as it is compression-optimized format.

## Http/2

- Use [Http/2](Protocols/Http.md). Latency improvement and packet size.

## Cors

- Avoid them by using Standard headers ("Authorization" header)
- Avoid them by using an ApiGateway so the Api services and WebApp will be hosted by the same dns.
- Cache CORS requests

## Caching

- ETag, Connection: Keep-Alive
- Enable Http Caching

## Server Physical Location

Far distance between server and client might cause a high latency.
For example, between Europe to Israel, avg latency is about 65 ms. between USA to Israel, the AVG latency is about 220 ms.

- Consider using a local server for you clients.
  - Use a Geography based DNS to route your clients to the closest server

## UDP vs TCP

- When data hermeticity is not important, use UDP since it's way faster.

## Pagination

- Some requests might carry large amount of payload
- If the client of those API prefers to get the first byte as fast as possible rather than getting the whole result, it's not a good idea to return the whole data in the response payload.

- When dealing with relatively static data, which can be easily ordered, it is easy to implement pagination mechanism with two parameters of limit=25&offset=50.
- Now imagine Facebook feed, when data is constantly changing by the time pass, the next page can be totally different, not even a direct continue to the previous page. Working with Ids, times, gaps - Very complicated
- (?? Research More)

## Bulk requests - Chunks

Good Practice only in case of working with an API with bad performance

- Splitting each request to multiple requests. Each inner request will get part of the data
- Make sure that no data is missing between each chunks
- Handle data duplication (Union)
- Each inner request should have the same retry policy as for all requests
