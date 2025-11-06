# The Document Database

## Core Concepts

* **NoSQL document-oriented database.**
* **Schemaless:** Flexible data schema.
* **BSON:** Stores data in a binary JSON format for efficient storage and traversal.
* Supports [[Replication]] and [[Sharding]] (discussed in [[MongoDB-Scalability & Features]]).

## Data Model Mapping

| Relational Term | MongoDB Term | Notes |
| :--- | :--- | :--- |
| Database | Database | Holds one or more collections. |
| Table | Collection | A collection of documents, usually with a similar structure. |
| Row | Document | A JSON-like object with key-value pairs. Max size is 16MB. |
| Primary Key | `_id` | Must be a unique identifier. Automatically assigned if not provided. |
| Foreign Key | Reference | Stored in a document to link to another (see below). |

### Example Document

```json
{
  "_id": ObjectId('66bf8436254ee06187149f49'),
  "name": "Paula",
  "birthday": ISODate("1985-06-05T23:59:00Z"),
  "hobbies": ["music", "movies", "sport"],
  "address": { // Embedded Document
    "street": "Av. Bases de Manresa, 61-73",
    "city": "Manresa"
  }
}
```

## Document Structure: Modeling Relationships

How to represent relationships between entities is key. We have two main strategies:

### 1. Embedded Documents (Denormalized Model)

Related data is stored _within_ the main document.

- **Pros:**
    - **Fast Reads:** Everything is in one place, avoiding lookups (like JOINs).
    - **Atomic Updates:** Updates to a single document are atomic.
    - Simplicity: Fewer collections/queries.

- **Cons:**    
    - **Duplication:** If embedded data is repeated, changes require updating multiple documents.
    - **Size Limit:** Documents have a 16MB size limit.

- **Best for:** One-to-One and bounded (non-growing) One-to-Many relationships (e.g., an address that only belongs to one user).    

### 2. References (Normalized Model)

Related data is stored in a _separate document_, and a field is used to store the `_id` of the related document.

- **Pros:**
    - **Normalized Structure:** Reduces duplication, making updates easier.

- **Cons:**
    - **Slower Reads:** Requires multiple queries or using the `$lookup` aggregation stage (which is slower than embedding).
    - **No Cross-Collection Atomicity** (unless using multi-document transactions).

- **Best for:** Large One-to-Many or Many-to-Many relationships to avoid duplication and document growth issues.

## Basic CRUD - Read Operations

Accessing the shell is done via `mongosh`.

- **Find One Document:** `db.students.findOne({"email": "paula@upc.edu"})`
- **Find Multiple Documents:** `db.students.find({"age": {$gte: 23}})`    
    - Can use comparison operators (`$eq`, `$gt`, `$gte`, `$in`, etc.) and logical operators (`$and`, `$or`, `$not`).
      
- **Projection (Selecting Fields):** The optional second argument to `find`/`findOne` specifies which fields to return (`1` for include, `0` for exclude). `db.students.findOne({}, {_id: 0, name: 1, email: 1})`
    - **Note:** `_id` is always returned unless explicitly excluded with `_id: 0`.

- **Querying Embedded Documents (Dot Notation):** Use dot notation to query fields inside an embedded document or array. `db.students.find({"courses.id": 101})`