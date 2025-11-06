A Key-Value database is the simplest form of a [[Non-relational Database]] (NoSQL).

- **Structure:** It fundamentally stores data as a collection of **key-value pairs**, essentially acting like a massive, persistent dictionary or hash map.

- **The Key:** The key is a **unique identifier** (like a primary key) used to retrieve the associated value. It is typically a simple string.

- **The Value:** The value can be anything—a simple string, a JSON object, a list, or even more complex data types like those offered by **[[Redis]]**.


## How It Works

1. **Read/Write:** All operations are based on the key. You _must_ know the key to get the value.

2. **Operations:** The core operations are extremely simple and fast:
    - **GET** (key) $\rightarrow$ Value        
    - **SET** (key, value)
    - **DEL** (key)

3. **Indexing:** Data is primarily indexed only by the key. This simplicity is what makes them so fast. Unlike relational databases, you cannot easily query based on the content of the _value_ (you can't ask "give me all values where the 'age' property is 25" unless the value itself is the key).    

## Key Advantages

- **Speed (Performance):** They offer extremely fast read and write access because the lookup process is a direct hash lookup by the key. This is why they are often used as **caches**.
- **Scalability:** They are easy to **horizontally scale** (sharding) by partitioning the data based on the keys across multiple servers.
- **Flexibility:** The value content can be flexible (schemaless).

## Common Use Cases

Key-Value stores are perfect for scenarios requiring low-latency lookups:

- **Caching:** Storing frequently accessed data to reduce load on the main, slower database. We often use the **[[EXPIRE]]** command here to set a Time To Live (TTL).
- **Session Management:** Storing user session tokens, preferences, and shopping cart contents.
- **Rate Limiting:** Using a key for a user ID and incrementing a counter to track request limits (**[[INCR]]** command).

_A great example of a Key-Value store is **[[Redis]]**._
