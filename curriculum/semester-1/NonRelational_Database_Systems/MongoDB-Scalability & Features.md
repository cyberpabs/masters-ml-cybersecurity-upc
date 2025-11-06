# Scalability and Advanced Features

## Replication for High Availability

**Replication** keeps identical copies of your data on multiple servers.
* **Replica Set:** A group of servers consisting of:
    * **One Primary:** Handles all write operations and most reads.
    * **Multiple Secondaries:** Maintain copies of the primary's data. Read operations can be distributed to these nodes to reduce load on the primary.
* **Fault Tolerance:** If the primary crashes, secondaries elect a new primary, minimizing downtime.
* **The Majority Rule:** Replica sets operate on majorities.
    * A primary is only stable if it can reach a *majority* of the set's members.
    * A write is only *safe* when it has been replicated to a *majority* of the set.
    * *Majority* = more than half of all members (e.g., in a 7-member set, the majority is 4).
    * **Avoid split-brain:** If a network partition occurs, only the side with the majority can elect a primary.

## Sharding for Write Scalability

**Sharding** (or partitioning) splits a dataset across many machines (shards).
* **Goal:** Achieves write scalability, allowing the cluster to store more data and handle more load than a single server.
* **Cluster Components:**
    * **Shards:** The actual MongoDB servers (machines) holding a subset of the data (**chunks**).
    * **`mongos`:** Routing processes that sit in front of the shards, hiding the clustering details from the application.
      
* **When to Shard:** When you need increased disk space, greater read/write throughput than a single server can handle, or load reduction.
* **When *Not* to Shard:** If the dataset fits comfortably on one server, or if performance can be fixed with better indexing/schema optimization.

## Aggregation Framework

The aggregation framework is MongoDB's analytics tool, a more performant alternative to the older MapReduce model.

* **Pipeline Concept:** It's based on a pipeline where documents are processed through a series of stages.
    `db.collection.aggregate( { stage1... }, { stage2... }, ... )`
* **Key Pipeline Stages:**
    * **`$match`**: Filters documents to pass only the ones that match the specified criteria (similar to a WHERE clause).
    * **`$group`**: Groups documents by a specified key and performs aggregate operations (like `$avg`, `$sum`).
    * **`$sort`**: Sorts the documents.
    * **`$project`**: Selects, renames, or creates new fields.
    * **`$lookup`**: Performs a left outer join to an *unsharded* collection in the same database (used to emulate a JOIN, often required for [[References]] data modeling).

## Indices
MongoDB uses **indices** to improve query execution speed by avoiding a full collection scan (COLLSCAN).
* **Trade-off:** Adding an index negatively impacts write operations (insert, update, delete) because the index must also be updated.
* **Syntax:** `db.collection.createIndex({ <field>: <sortOrder / type> })`
* **Index Types:**
    * **Single-field:** Index on one field.
    * **Compound-field:** Index on multiple fields (order matters). Used to match the sort order of the query.
    * **Geospatial:** Special indices (like `2dsphere` or `2d`) required for proximity queries (`$near`, `$geoWithin`).