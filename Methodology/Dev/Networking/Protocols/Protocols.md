# Communication Protocols

Http vs MSMQ vs WebSockets

## OnDemand vs Event Driven Communication

There are two different types of requests:

- On Demand
  - Client is waiting for a response. As long as he waits, as the chances he will get pissed off.
- Event

  - Something has happened in the world, nobody knows when - thus nobody is waiting for it.
  - This is an event, and it triggers a request to your services to notify you about it. The services get the data, process it and do whatever they want.
  - For these type of request we can use a Queue tool that will help us manage all the events more easily and safely.

## Push Communication ( vs pull)

When a server has to initial a request to his client, what makes him the client and the "client" as the server, and this request could be triggered anytime, there are few options:

### Push Communication Implementations ?

- Http pooling
  - The client constantly asking the server if there is a new data
  - Cons - A lot of traffic
- Http long pooling
  - The client sends a single http, the server holds it until he got a response.
  - Cons: Holding an open HTTP-TCP session
- WebSockets
  - The client notify the server for it's existence. A duplex channel is opened.
  - Both of them can transfer data in this channel whenever they want.
  - WebSockets are way faster than HTTP
  - Cons
    - Complicated to implement
    - (?) Less Hermetic -> packets can be lost.

### Choosing between Http polling(shot/long) vs WebSocket push

- WebSocket is better when servers are on heavy load
  - Many clients - more load on server
  - When clients have to get updates immediately (shorter polling intervals) - more load on server
  - Server doesn't have many "data updates" - client keeps the requests - more load on server
- On low load, since adding Pushing Mechanism is complicated, sometimes it doesn't worth it, so we should keep the simple solution with http polling
- Replication
  - (?) Use Http Polling since in Push WebSockets, requests are less hermetic.
- You can combine Push and Pull
  - For example, using 99% of the time push notification, while one in a while make sure all data has arrived by regular http request.
