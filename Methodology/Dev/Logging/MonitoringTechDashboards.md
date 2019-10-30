# Monitoring Tech Dashboards

## Tools

- Kibana
- Graphana
- Logz.io

Kibana vs Graphana - It seems like Graphana is taking the lead.

## Must have Tech-Visualizations

- Each logical environment should have a the same visualizations logic, but in a separate dashboard.
- Client Latency
  - They are far far away from us. Some of them will abandon you if everything is so SLOW for them.
- All IO
  - Types:
    - Http / WebSockets / Databases / MSMQ ...
    - Storage
  - Total Time
  - Average Time
  - Max/Min Time
  - O(1) / Linear / Exponential
  - Explore request by their IO trace
- Errors
  - Critical / Bad Request
  - Errors Grouping by type - otherwise when you get 19847 errors in one minute of the same type, you won't notice of these nice 2 of a different type

## Must have Business Visualizations

Will be discussed in the 'Product' section
