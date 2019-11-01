# Choosing a DataBase

## Data Model

What native data structure suits the DataModel the most?

- Relational
- Graph
- Key Value

Data types

- Schemaless / Strict-Schema
- Geo-Spatial
- Text based
- Types with large volume
- Custom Types

## Data Behavior

- Is ACID important for you?
  - Atomic - Transactions
  - Isolation - Race condition of multiple transactions
  - Consistency - Always consistent / Eventually-consistent
    - Do your app design for eventually-consistent data?
    - Data constraints, FK, Cascades, Triggers
  - Durability - Will be committed even if the DataBase crashes in the middle of a transaction.
- Data Modification rate (Insert, Update, Delete)
- Size of the Data. Volume scale (Static/Linear/Exponential)
  - Scale Up / Scale out
- Queries profile
  - Join queries between tables/collections?
  - Hierarchy queries?
- High Availability? Disaster Recovery?
  - Supports Active Active? Cross-Regional Active Active?
- Caching? (SuperFast Queries - like Redis)
- Scheduler/Job/Task/Cron

## Infrastructures

- Does it have a Manage-Cloud service?
  - If you have to host and mange it by your self, it's a whole new
- Is it possible to run it locally with docker?

## Usual Considerations

- Stability of the DataBase
- Who's behind it
- Community
- OpenSource or not
- Support
- Price
