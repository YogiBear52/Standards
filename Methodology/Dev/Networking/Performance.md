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
- If the client of those API prefers to get the first byte as fast as possible rather than getting the whole result, it's not a good idea to return the whole data in the response payload.

- When dealing with relatively static data, which can be easily ordered, it is easy to implement pagination mechanism with two parameters of limit=25&offset=50.
- Now imagine Facebook feed, when data is constantly changing by the time pass, the next page can be totally different, not even a direct continue to the previous page. Working with Ids, times, gaps - Very complicated (?? Research)
