# The Key-Value Store

## Overview

* **REmote Dictionary Service (Redis)** is an **in-memory [[Key-Value Database]].**
* **Fast:** Because it's primarily in-memory, it provides very high-speed operations.
* **Features:** Fast key-value store, support for complex [[Redis Data Structures]], [[Pub/Sub]], blocking queues, and Full-Text Search (via RediSearch).

## Persistence (Memory with Disk Backup)

Although it's an in-memory database, it uses disk for persistence to prevent data loss:

1.  **Snapshots:** Copies of the entire system state at a point in time.
2.  **Append Only File (AOF):** A journal of all write operations that can be used to "roll forward" the database from a snapshot in case of failure.

## Use Cases

Redis excels where speed and temporary storage are key:
* Cache data (e.g., using `EXPIRE` to set a Time To Live).
* Store session information and user preferences.
* E-commerce shopping carts.
* Rate limiting (using `INCR` to count requests).

## Basic Operations (String Type)

Almost all commands query data only by the key.

| Command | Description | Example |
| :--- | :--- | :--- |
| `SET`/`GET` | Set and get a key-value pair. | `SET user paula` / `GET user` |
| `DEL` | Delete a key. | `DEL user:paula` |
| `EXPIRE`/`TTL` | Set a time-to-live in seconds/check remaining time. | `SET session foo EX 60` / `TTL session` |
| `INCR`/`DECR` | Increment/decrement the value (if it's an integer). | `INCR counter` |

## Redis Data Structures

The "value" can be more than just a simple string:
* **Hash:** A collection of field-value pairs (like an object/document). Great for storing objects with a few fields.
    * `HSET user:paula name "Paula Fuster" age 24`
    * `HGETALL user:paula`
      
* **List:** An ordered collection of strings. Can be used as a:
    * **Stack (LIFO):** `LPUSH` (push left) and `LPOP` (pop left).
    * **Queue (FIFO):** `RPUSH` (push right) and `LPOP` (pop left).
    * **Blocking Queue:** Commands like `BRPOP` block the client until an element is available or a timeout is reached.
      
* **Set:** An *unordered* collection of *unique* strings. Useful for performing operations like unions, intersections, and membership tests.
    * `SADD users:courses:a user:paula user:josep`
    * `SMEMBERS users:courses:a`
      
* **Sorted Set (ZSET):** A set where each member is associated with a score (float), allowing elements to be ordered by score. Great for leaderboards.

## Advanced Data Structures

* **HyperLogLog:** A *probabilistic* data structure that estimates the **cardinality** (number of unique elements) of a set, using very little memory (up to 12 KB).
    * `PFADD` / `PFCOUNT` / `PFMERGE`
      
* **Bloom Filter:** A *probabilistic* data structure that tests whether an element is a member of a set. It can **guarantee the absence** of an item, but only **estimate presence** (false positives are possible). Used for filtering non-existing keys or malicious URLs.

## Pub/Sub & Pipelining

* **[[Pub/Sub]]:** A publish-subscribe messaging system. A client can `SUBSCRIBE` to a channel, and another can `PUBLISH` a message to it. Used for notifications, real-time updates, etc.
* **[[Pipelining]]:** A technique to improve performance by sending multiple commands at once without waiting for the server response for each one. This reduces **Round Trip Time (RTT)**.