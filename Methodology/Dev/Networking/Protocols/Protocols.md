# Communication Protocols

Http vs MSMQ vs WebSockets

## OnDemand vs Event Based Communication

There are two different types of requests

- On Demand
  - Client is waiting for a response. As long as he keeps waiting, as the chances he will get pissed off.
- Event based
  - Something has happened in the world, nobody known when- thus nobody is waiting for it.
  - This is an event, and it triggers a request to your services to notify you about it. The services get the data, process it and do whatever they want.
  - For these type of request we can use a Queue tool that will help us manage all the events more easily and safely.
  - These queue tool are using a different protocol, more efficient one than HTTP - MSMQ.
  - This is a Sub-Pub mechanism.

## Push Communication ( vs pull)

When a server has to send it's client data
And the data is an event-driven, thus, can be triggered anytime, there are few options:

### How do we implement Push communication ?

- Http pooling
  - The client constantly asking the server if there is a new data
  - Cons - A lot of traffic
- Http long pooling
  - The client send a single http, the server holds it until he got a response.
  - Cons: Holding an open HTTP-TCP session
- WebSockets
  - The client notify the server for it's existence. A duplex channel is opened.
  - Both of them can transfer data in this channel whenever they want.
  - WebSockets are way too fast than HTTP
  - Cons
    - Complicated to implement
    - Less Hermetic -> packets can be lost.

### Choosing between Http polling vs WebSocket push

- Replication
  - You might think that when constantly replicated data from one API to another, we want to use Push method, because we have no idea when a new data will be inserted. But when replicating data, hermetic replication is more important. We cannot allow a lose of data because there was a network connection and the PUSH notification has dropped and will never reach the replicator.
- Pushing is better when server are on heavy load
  - Many clients - more load on server
  - Each client has to get immediate updates (shorter polling intervals) - more load on server
  - Server doesn't have many "data updates" - client keeps the requests - more load on server
- On low load, since adding Pushing Mechanism is complicated, sometimes it doesn't worth it, and we keep the simple solution with http polling
- You can combine Push and Pull
  - For example, using 99% of the time push notification, while one in a while make sure all data has arrived by regular http request.
