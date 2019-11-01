# SLA (Service License Agreement)

## [Availability](https://en.wikipedia.org/wiki/High_availability)

- Uptime Percentage
  - two nines (99%) - downtime of 3.65d
  - two nines five(99.5%) - downtime of 1.83d
  - five nines (99.999%) - downtime of 5.26 minutes
    - performance-sensitive industries like finance and ecommerce
  - six nines (99.9999%) - downtime 31.56 seconds a year
  - \*\* most of the downtime is spent on recover/repair
- Time to alert in advance before a shutdown / maintenance

## Responsiveness

- Total time to execute a request.
  - AVG + Max
  - Per type of request
- Maximum number of errors(500 internal)

## Other Points in the Agreement

- Refund
  - Credit per each percentage of responsiveness/Uptime violation

## SLA enforcement

- Most of the times the API side - more to loss.
- In cases when the API is so critical, the client side too
