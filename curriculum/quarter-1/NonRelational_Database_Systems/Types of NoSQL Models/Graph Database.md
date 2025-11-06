A Graph Database is a [[Non-relational Database]] (NoSQL) that uses **graph structures** with nodes and edges (relationships) to represent and store data.

- This model is optimized for working with **highly interconnected data**, where the relationships between entities are just as important as the entities themselves.    
  
- **Neo4j** is the most widely recognized example, known for its **native graph processing** capabilities.    

## The Core Entities

A graph database is built on three fundamental entities:

1. **[[Node]] (Vertex):** Represents entities or objects in your domain.    
    - Example: A `Person`, a `Course`, or a `Location`.        
    - They have at least one **Label** (like a type or table name) and can hold **Properties** (key-value pairs) (e.g., `name: 'Paula'`, `age: 24`).

2. **[[Relationship]] (Edge):** Explicitly defines the connection between two nodes. This is the key difference from other databases; the links are first-class citizens.    
    - Example: A person **\[:ENROLLED_IN]** a course.        
    - They have a **Type** (e.g., `ENROLLED_IN`), a **Direction**, and can also have **Properties** (e.g., `grade: 8`).

3. **[[Path]]:** A sequence of nodes and relationships that are connected in order. Querying a path answers complex questions about how entities are related (e.g., "What is the shortest path between user X and user Y?").    

## Key Features

- **ACID Compliance:** Unlike many NoSQL types that favor eventual consistency, graph databases typically aim for **ACID** properties to ensure data integrity.

- **Vertical Scaling:** Graph databases usually scale **vertically** (adding more resources to a single server) rather than horizontally (sharding) because the relationship data is often stored on a single machine for fast traversal.

- **Cypher Query Language:** The standard language for querying Neo4j. It is a declarative language focused on **pattern matching** using ASCII art syntax: `(node)-[relationship]->(otherNode)`.
  
## Use Cases

Graph databases excel in domains where the importance of the data lies in its **interrelationships**:

- **Social Networks:** Finding friends of friends, community detection, or degrees of separation.  
- **Recommendation Systems:** "People who watched this movie also watched that movie."
- **Route/Logistics Applications:** Determining the shortest, fastest, or cheapest path between two points.
- **Fraud Detection:** Identifying unusual patterns or rings of related accounts/transactions.

_A great example of this is **[[Neo4j]]**._
