# Mongo

- Data Modification
  - Mongo is designed for fast and intense data modifications(specially insert), thus fully Async by default
  - Use WriteConcern to mange the Async level.
- Do the app is designed to work as the data is Eventually-Consistent
- Data Relations
  - Mongo is not very good with Join Queries of tables in a relation.
  - One to Many by reference vs embedded
    - Is the Many column referenced by other tables?
    - Is it One to Some or One to Squillions?
      - It will be hard to make Join queries with One to Squillions.
- Schema Validators
- Transactions
  - Possible since Mongo 4.x. Performance penalty
- GridFS vs Storage
  - Mongo can help you with saving large object, but don't push it too much, it's not a storage-calibrated tool.

(?? Research more)
