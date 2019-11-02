# Data Bases

- Data Bases have became more easy to use. Manged Databases are created in within minutes thanks to our cloud providers. It's easy to maintain, to copy data from one to another, to switch DataBases and so on..
- Therefore, nowadays, Data Bases are used more as an Index rather than a Storage+Index
- Modern Architecture adopt the concept of [Event Driven Architecture](../Architecture/EventDrivenAritecture.md), where Data is saved to a BUS, there it is stored. From there, it pushes the data to all indexes, per the need of our apps.

## General

- Compress data
- Encrypt sensitive data
- Keep low latency between the DataBase and the services using it

## Data Model Corruption

- Can you modify the data so it will become corrupted?
- Design the DataBase, Schemas, Relations, Constraint to reflect the how the data really behave

(?? Some examples)

## Security

- Do not expose the DB to public internet
- Give as minimum permissions you can to each user.
  - In addition, it will protect applications of harassing the DataBase (e.g DROP permissions)

## High Availability

- Data backup.
  - Try to simulate the backup restoring operation, since it is so important but organizations keep failing doing it.
- Disaster Recovery
- Active-Passive, Active Active Architecture
