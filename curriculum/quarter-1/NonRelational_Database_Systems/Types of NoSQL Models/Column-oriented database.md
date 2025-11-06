A Column-oriented database (sometimes called a Column Family store) is a type of [[Non-relational Database]] that organizes data around **columns** rather than rows.

- In a traditional RDBMS, data is stored by row: all the data for one record is grouped together on disk.
- In a Column-oriented database, all the values for a **single column** are stored together.

## Data Structure and Features

- **Row Key:** Each row still has a unique **key**.
- **Flexible Columns:** Each row can use a different set of columns, it's **schemaless** at the row level, which offers flexibility.
- **Column Families:** Columns are often grouped into "families" based on how frequently they are accessed together, which helps optimize data retrieval.
- **Atomicity:** Usually guaranteed at the **row-level**, meaning any changes to a single row are atomic.

## The Trade-off: Reads vs. Writes

|**Feature**|**Column-oriented DB**|**RDBMS (Row-oriented)**|
|---|---|---|
|**Read Speed**|**Fast** (When accessing only a few columns)|Slower (When accessing only a few columns)|
|**Write Speed**|Slower (Requires scattering data across columns)|Fast (Writes data sequentially in a single row)|
|**Storage Efficiency**|Highly efficient for **compression** since data within a column is often the same type and has similar values.|Less efficient for compression.|

## Use Cases

Column-oriented databases are optimized for workloads where you need to perform analysis on large volumes of data, accessing only a small subset of the total attributes (columns).

- **Business Intelligence (BI) and Analytics:** Perfect for storing and querying massive amounts of data for reporting, where you might only need `user_id` and `purchase_amount` out of a thousand columns.
- **Event Logging:** Storing log files, time series data, and telemetry, where the volume is high and the queries often focus on specific metrics across many entries (e.g., "count all errors where status code is 500").

_A well-known example of this type of database is **[[Apache Cassandra]]**._
