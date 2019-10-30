# LoadBalancer - High Availability

- Usually comes together as a Feature in API Gateway

## [Algorithms](https://kemptechnologies.com/load-balancer/load-balancing-algorithms-techniques/)

- Round Robin
- Weighted Round Robin
  Weighted Round Robin builds on the simple Round Robin load balancing method. In the weighted version, each server in the pool is given a static numerical weighting. Servers with higher ratings get more requests sent to them.
- Least Connection
  Neither Round Robin or Weighted Round Robin take the current server load into consideration when distributing requests. The Least Connection method does take the current server load into consideration. The current request goes to the server that is servicing the least number of active sessions at the current time.
- Weighted Least Connection
  Builds on the Least Connection method. Like in the Weighted Round Robin method each server is given a numerical value. The load balancer uses this when allocating requests to servers. If two servers have the same number of active connections, then the server with the higher weighting will be allocated the new request.
- Agent-Based Adaptive Load Balancing
  Each server in the pool has an agent that reports on its current load to the load balancer. This real-time information is used when deciding which server is best placed to handle a request. This is used in conjunction with other techniques such as Weighted Round Robin and Weighted Least Connection.
- Active/Passive
  - Prefer Active/Active if your application can handle it
  - When other resources are used only for certain times, while the are relatively slow and your prefer not to use them if not needed.

## BP

- Register services dynamically
- Can put a service in maintenance mode - stop receiving new requests and removes server from pool when no more requests are currently executing
  - Good for Deploying
