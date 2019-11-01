# General Data Bases Best Practices

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
