A document-oriented database is a type of [[Non-relational Database]] (NoSQL) that stores data in structured **document** format, most commonly **JSON** (JavaScript Object Notation) or its binary version, **BSON**.

- **Document:** This is the core unit of storage. Think of it as a single, self-contained record (like a row in an RDBMS, but far more flexible).

- **Collection:** Documents are grouped into collections, which are similar to tables, but the documents within a single collection do _not_ have to share the exact same structure (this is the **schemaless** feature).

## Key Characteristics (Why use it?)

1. **Flexible Schema (Schemaless):** This is the biggest selling point. Unlike RDBMS tables, documents in a collection can have different fields. This allows for rapid development and easy adaptation as application needs change.

2. **Embedded Data/Denormalization:** Related data (like an address or a list of hobbies) can be **embedded** directly within the primary document. This eliminates the need for expensive **JOINs** typical in RDBMS, making read operations extremely fast.

3. **Horizontal Scalability:** Document databases like **[[MongoDB]]** are designed to be easily **sharded**, distributing the data across many machines for massive scaling.

## Data Model

|**Relational Term**|**Document DB Term**|**Notes**|
|---|---|---|
|Database|Database|The container for collections.|
|Table|**Collection**|A group of documents.|
|Row|**Document**|The self-contained unit of data (JSON/BSON object).|
|Primary Key|**`_id`**|A unique identifier for every document.|

## Modeling Relationships

Since there are no JOINS, relationships are handled in one of two main ways, depending on the use case:

1. **Embedding (Denormalization):** Placing related data directly _inside_ the main document (e.g., embedding a user's address object inside the `User` document).    
    - **Pro:** Very fast read performance (one query).
    - **Con:** Leads to data duplication and can make updates complicated.

2. **References (Normalization):** Storing a link (the `_id`) to a document in another collection (e.g., storing a list of `Course` IDs inside the `Student` document).    
    - **Pro:** Reduces data duplication.
    - **Con:** Requires multiple queries or using the slow **`$lookup`** stage in the [[MongoDB-Scalability & Features|Aggregation Framework]] to resolve the reference.

_The most popular example of a document-oriented database is **[[MongoDB]]**._
