# LoadBalancer - High Availability

- Usually comes together as a Feature in API Gateway

## [Algorithms](https://kemptechnologies.com/load-balancer/load-balancing-algorithms-techniques/)

- Round Robin
- Weighted Round Robin

  builds on the simple Round Robin load balancing method. In the weighted version, each server in the pool is given a static numerical weighting. Servers with higher ratings get more requests sent to them.

- Least Connection

  Neither Round Robin or Weighted Round Robin take the current server load into consideration when distributing requests. The Least Connection method does take the current server load into consideration. The current request goes to the server that is servicing the least number of active sessions at the current time.

- Weighted Least Connection

  Builds on the Least Connection method. Like in the Weighted Round Robin method each server is given a numerical value. The load balancer uses this when allocating requests to servers. If two servers have the same number of active connections, then the server with the higher weighting will be allocated the new request.

- Agent-Based Adaptive Load Balancing

  Each server in the pool has an agent that reports on its current load to the load balancer. This real-time information is used when deciding which server is best placed to handle a request. This is used in conjunction with other techniques such as Weighted Round Robin and Weighted Least Connection.

- Active/Passive
  - Prefer [Active/Active](../Architecture/ActiveActive.md) if your application can handle it
  - Prefer Active/Passive, when one of the routes is pointing to relatively slow resources and your prefer not to use them if not needed.
  - (?? Research more)

## BP

- Register services dynamically
- Can put a service in maintenance mode - stop receiving new requests and removes server from pool when no more requests are currently executing
  - Good for Deploying
- Health Check
  - Don't just send a 200 OK, check the App general health.
    - Check if dependencies are working.
    - Storage, DB, External APIs ...
    - Use the new Health Check response standard
  - Configurable rate of healthcheck intervals and determination of time of death.
    - Most of the time the default setting will be just fine.
    - In case your App is closer to real-time, you may consider set it to stop send the servers request after less failure health checks.
  - Liveness and Readiness
  - Fast healthcheck response.
