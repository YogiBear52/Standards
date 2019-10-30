# Servers Load and Performance

- Prepare for worst case scenarios when load is high.
- Make sure we meet our SLA requirements.

For that, we must know our current load and try to predict the worst case sangria when the load is high. Are we prepared?

- Load/Stress Tests
  - Simulates real time traffic load on your services
  - Simulates intense time traffic load on your services

## Regular Times (Routine)

- Avg clients
- Avg requests traffic
- DataBases data size`
- Client natural growth - Client increase estimation.

## Intense Time (Heavy load)

- When? Specific times?
- Avg Clients?
- Avg requests Traffic?
- DataBases data size

## Load and Performance Tests

### Load Tests

No load test will ever simulate real situations.

- Traffic diversity
- Traffic Peeks
- Different usage of API
- It's like a war - UNKOWN BLA BLA

What can we do:

- Estimate our clients number
- By calculating the avg traffic of each client on regular times, we can roughly predict the overall traffic on intense times
- Use different flows and scenarios on you system.
  - Make heavy load scenarios, Medium and Low - as real as possible.
  - Number of times to invoke each scenario - as real as possible.
- Simulate concurrency - as real as possible.
- Always test the same environment, with the same resources (CPU,RAM,Network Bandwidth, Number of containers), of course a prod-like environment.
- Make sure you insert the amount of estimated data to DataBase
  - So you will also test your DataBase
  - Low quality queries,indexes and DB bad practices, tend to make queries slower and slower the more data stored.
- Run Load and Performance tests on a daily basis(Connect them to your CI), otherwise they will just get old and not relevant.
- Run Load and Performance tests on your production from time to time.
  - These tests should not check the edge capabilities of your service, but simulate real times scenarios.
  - if you are afraid of doing so, it means your production app will suffer from bad performance on important times.
    - So you app better crash now, than on intense times.

Conclusion of load tests:

- Same response time for all request? (Performance)
  - After what load decrease in performance?
- Maximum/Required requests our service can handle - Concurrency rate.
- How many resources will we need?
  - Number of containers / VM - CPU RAM - we need more
  - Auto-Scale - don't spend resources only for one day in a year when traffic is high.
    - If Auto-Scale is not an option, add the resources just before the event.
  - Is out system reach the 100% RAM or 100% CPU while checking it's maximum requests rate?
    - If not, it means our application doesn't utilize all of its resourcing. It usually happens because of bad use of Async IO(Reference to Async Await).
- Do we meet our SLA requirements?

(?? Research more)
