# External API

It's so hard to work with External APIs
A major time of your development time is spent on managing and working with the External APIs:

- Breaking changes
- Errors
- Downtimes
- Performance issues
- Bad Documentation

A project with more than 10 External API is considered to be very large a hard to maintain.

There are some question you must answer before connecting your app or making a contract with an External API

- Is this API already deprecated? Does it have a replacement? Shut-Down due time?

Put every External API in few scales

1. Trust level from 1-10
   - The provider's given support level
   - API flakiness
   - Do you curse the API and it's providers on a daily-basis?
2. How crucial from 1-10 is this API for your application?
3. Does it have a defined SLA?
   - Are you fine with this SLA?
   - Have you every checked the API can stand in your worst estimation of Performance and Load?
     - Expected SLA vs Actual SLA
   - Is the provider committed to the SLA?
     - Has something to loose (Refund)
     - It's their main business, very important for them

This rank will help you evaluate how much effort on Monitoring and Testing you have to invest on this API.

1. Hermetic tests to this API from 1-10
   - API tests, E2E, unit tests to your API access code..
2. [Monitoring the SLA](SLA.md)

For API with bad rank you should have a good rank in Testing and Monitoring.

- Contract - If this API is so crucial to you app, don't use it unless the contract is good (SLA+Support) for you app needs
- In case of SLA violation, or bad performance trend, Monitor, extract a nice detailed report out of your monitors. Send it to their support, show them the bad trend or the SLA violation. Make them realize you are a serious customer.
