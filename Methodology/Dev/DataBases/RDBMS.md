# RDBMS Data Bases

## PostgreDB vs Oracle

Cons for Postgre:

- Larger community
- More modern than Oracle
- Adopted by cloud providers - Manged DB
- Its a tie regards all related to Performance and Capabilities
- PostgreDB can run locally with docker

## Performance

- Indexes
  - Choose the right type of index, depends on the column Type
    - Regular BitTree
      - Will be used in most of the cases
    - Bitmap - enums
      - Good Performance on small set of data which barley modified.
    - Sort Asc/Dec
      - In case of an OrderBy query, the index is already ordered.
    - Compound
      - Querying on multiple fields together.
    - Specific - Textual/GeoSpatial
  - Rebuild indexes (BTree Traversal)
    - After data modification some indexes are not self-optimizing themselves immediately.
    - It's an heavy action, make sure you don't lock the DB and you schedule it to low-active times.
- Partitions
  - Splits tables two multiple partitions(sub-tables) by a condition.
  - Global indexes for the whole table and inner indexes for each partition.
  - If the query matches the partition query, it will run only on some partitions, which suppose to significantly reduce the amount of data querying.
- Parallelized
  - Allow DB to run queries in parallel.
  - Use it wisely, by the specific DB's Best Practices
- Run Data Statistics
  - Constantly collect statistics on your data, it will improve the Optimizer brain
- In Memory Column
  - Column oriented DataBases
  - Good when actions on the table are column oriented and not row-oriented, since, storage, the whole column data located in on the same "Array"/"Memory Segment".
  - Casandra and HBase Databases are fully column oriented databases.
- Connection/Session pooling
  - Creating a new connection to DB is an heavy task
  - Optimize pool's creation and closing connection rate by your needs.
- Materialized View
  - Just like a regular View, but data is stored in a Regular Table
  - Queries that matches the View query, will automatically route to this table, which suppose to be more optimized.
  - Its a replication. High storage.
- Query cache
  - Cache queries templates, to save the Optimizer time
- Query Response Data Streaming
  - In case client, when querying, needs the whole result, you have nothing to do but wait for the query to complete.
  - In case client, when querying, needs to get first result of the query as fast as possible, stream the data.
