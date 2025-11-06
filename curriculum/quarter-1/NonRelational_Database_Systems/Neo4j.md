# The Graph Database

## Overview

* **Neo4j** is a **native [[Graph Database]]**. This means it implements a true graph model all the way down to the storage level.
* **Use Cases:** Highly related data where the connections are as important as the data itself:
    * Social networks
    * Recommendation systems (e.g., "People who bought X also bought Y")
    * Route applications
    * Fraud detection

## Core Entities of a Graph

The graph consists of three main entities:

1.  **[[Node]]** (The Vertex): Represents entities or objects of a domain (e.g., Person, Course).
    * Has at least **one label** (like a table name).
    * Can have **properties** (key-value pairs) (e.g., `name: 'Paula'`, `age: 24`).
      
2.  **[[Relationship]]** (The Edge): Describes how two nodes are connected.
    * Has **one type** and **one direction**.
    * Can also have **properties** (e.g., a relationship type `:ENROLLED_IN` could have a property `grade: 8`).
      
3.  **[[Path]]**: A sequence of nodes and relationships connected in order, showing how entities are related.

## Cypher Query Language

**[[Cypher]]** is the declarative language used to query Neo4j.
### Basic Syntax

* **Nodes:** Use parentheses `( )` with optional label and properties.
    * `(p:Person)`
    * `(s:Student {name: 'Paula'})`
      
* **Relationships:** Use arrows to denote type and direction.
    * `-[r:ENROLLED_IN]->` : relationship `r` of type `ENROLLED_IN` from source to target.
    * `<--` : specifies the direction (going from target to source).
    * `--` : matches any direction.
      
* **Hops/Length:** The `*` operator specifies the number of relationship hops.
    * `(p)-[*]->(a)` : any length
    * `(p)-[*2]-(a)` : exactly 2 hops (in either direction)
    * `(p)-[*1..3]-(a)` : between 1 and 3 hops

### CRUD Operations

| Operation | Syntax Example | Notes |
| :--- | :--- | :--- |
| **CREATE** Node | `CREATE (c:Course {id: 101, name: 'NoSql DB'})` | Creates a new node with a label and properties. |
| **CREATE** Relationship | `MATCH (c:Course{id: 101}), (s:Student{name: 'Paula'}) CREATE (s)-[:ENROLLED_IN {year: 2025}]->(c)` | Needs to `MATCH` existing nodes first. |
| **READ** (Query) | `MATCH (:Course{id:102})<-[:ENROLLED_IN]-(s) RETURN s.name` | The core operation. `MATCH` finds the pattern, `RETURN` outputs data. |
| **UPDATE** (Set) | `MATCH (c:Course {id: 101}) SET c.description = 'new text'` | `SET` is used to add or modify properties/labels. |
| **DELETE** | `MATCH (s:Course {id: 101}) DETACH DELETE s` | `DETACH DELETE` removes the node *and* any associated relationships. |
