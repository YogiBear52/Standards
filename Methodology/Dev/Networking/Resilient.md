# Resilient Networking

We are using network requests more often because we want a dynamic website and thanks to the multi services architectures (MicroServices).

Failures happens within the wire, routers.
Errors are sent from flaky APIs
We must handle it, we must reduce the amount of errors returning to our users.

F -- > B --> B --> B

## What can we do?

- Retry
  - on real HTTP timeout
    - API has sent an timeout
    - we should set a timeout to each type of request
  - on Failure
  - on our timeout
    - so we can send another request while waiting to all others
  - Exponential back-off
    - Because things are bad, maybe we make it worse
  - Retry cancel
    - Retry --> Cancel previous request because the API is already falters. Letting him run two requests simultaneously might not be the best choice.
    - Or, if you don't feel pity of the API, Keep old requested open and return the first response out of all requests.
- Service On-Request-Canceled
  - Every service, within a request context must listen to the Http Request Cancellation, and if it's client has cancelled the request, we must stop our request too, including all the IO that have been sent by it.
  - Otherwise, the retry policies will just make ton of load in the system.
- Timeout on Timeout
  - Make sure the first request timeout is greater than the service total timeouts (including retries) of his APIs.
  - Otherwise, the client will cancel each request before the server got to execute it's retry policy.
- Get a resource is easy. What about Creating requests, Update or Delete requests ?
  - So we send 5 deletes. one of them will eventually catch. Same for PUT
    - It will spam with errors about deleting an not-existing.
  - Post - can create multiple resources. Really bad.
  - Per-Situation
    - Maybe after a long timeout
- User client Retry
  - MicroServices transactions
  - We spent so much time waiting, we have to let the user decide.
  - Complicated situations like POST, PUT, DELETE.
- User Queue tool to manage all the requests.
  - It will solve most of the problems, but has poor performance for on-Demand requests.
  - Another tool to maintain.

## Tools

- C# - Polly, RxNet
- Typescript - RxJs
