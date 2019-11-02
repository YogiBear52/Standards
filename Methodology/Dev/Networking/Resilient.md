# Resilient Networking

- The Amount of network requests is growing
  - Micro-Services
  - More dynamic websites

Request failures always happen!

Failures happens within the wire, routers.
Errors are sent from flaky APIs.

We must handle it, we must reduce the amount of errors returning to our users.

F -- > B --> B --> B

## What can we do ?

- Retry
  - The API response with a timeout
  - On Failure
  - On our internal timeout
    - so we can send another request while waiting to all others
  - Exponential back-off
    - Because things are bad, maybe we make it worse
  - Retry cancel
    - Retry --> Cancel previous request before sending another one. Since the API is already falters. Letting the server run two requests simultaneously might not be the best choice.
    - Or, if you don't feel pity of the API, Keep old requested open and return the first response out of all requests.
- Listen to Service On-Request-Canceled
  - Every service, within a request context must listen to the Http Request Cancellation, when request is cancelled by the client, we must stop our request execution, including all the IO that has been sent by it.
  - Otherwise, the retry policies will just make ton of load in the system.
- Timeout on Timeout
  - Make sure the first request timeout is greater than the service total timeouts (including retries) of his APIs.
  - Otherwise, the client will cancel each request before the server got to execute it's retry policy.
- Getting a resource is easy. What about Creating requests, Update or Delete requests ?
  - No problem! send 5 deletes. one of them will eventually catch. Same for PUT
    - It will spam with errors about deleting an not-existing.
  - Post - can create multiple resources. Really bad.
  - Per-Situation
    - Perhaps after setting long internal timeout
- Client GUI Retry
  - GUI button of "Retry doing ... "
  - [MicroServices transactions](../Architecture/MicroServices/Transactions.md)
  - When the client has spent too much time waiting, we have to let him decide what to do.
  - Complicated situations like POST, PUT, DELETE.
- User Queue tool to manage all the requests.
  - It will solve most of the problems, but has poor performance for on-Demand requests. [Protocols](Protocols/Protocols.md)
  - Another tool to maintain.

## Tools

- C# - Polly, RxNet
- Typescript - RxJs
- ApiGateway - Can execute retry policies
