# Introduction

## What is Big Data?

Big Data refers to datasets that are too massive or complex for traditional data-processing software. The key characteristics are the **3 Vs**:

* **Volume**: A massive amount of data being generated and stored (e.g., IDC predicts 163 ZB by 2025).
* **Velocity**: Data is generated quickly and needs to be processed fast (e.g., Twitter generating 12 TB/day).
* **Variety**: Various types and formats of data, often unstructured or semi-structured.

## RDBMS Review (Why We Need Alternatives)

Relational DataBase Management Systems (RDBMS) have been the standard since the 1980s.

**Core Ideas:**
* **Data Model:** Based on tables and relationships (using JOINs).
* **Normalization:** Data is typically normalized to reduce redundancy.
* **ACID Compliance:** Guarantees data integrity.

### The Problem: Scaling RDBMS

When data volume and velocity grow, traditional RDBMS struggle to scale. While some techniques like *sharding* (splitting data across machines) were attempted, they often failed for three reasons: cost, inability to demonstrate necessary scalability, and the fundamental constraint of **ACID compliance** itself.

### CAP Theorem

This theorem explains the fundamental trade-offs when designing a distributed system like a modern database: **it is impossible for any shared data-system to guarantee simultaneously all three properties in the event of a network partition.**

1.  **Consistency (C):** Once data is written, all future read requests will contain that data (Atomic Consistency).
2.  **Availability (A):** Every request received by a non-failing node must result in a response.
3.  **Partition Tolerance (P):** The network is allowed to lose arbitrary messages between nodes (i.e., network "partitions" can happen).

**Conclusion:** Since the internet is an *imperfect network* (meaning **P** is non-negotiable), a system must choose between strong **C**onsistency and global **A**vailability.

## Introduction to NoSQL

NoSQL is a term for databases that deviate from the RDBMS model, typically by relaxing the ACID constraints (specifically by sacrificing C for A and P) to achieve massive scalability and better performance for certain workloads.

### NoSQL Data Models Overview

| Model Type                         | Data Structure                    | Key Features                                                          | Examples         |
| :--------------------------------- | :-------------------------------- | :-------------------------------------------------------------------- | :--------------- |
| **[[Key-Value Database]]**         | Key-Value pairs (like a hash map) | Simple CRUD, fast reads, horizontal scalability (sharding).           | **[[Redis]]**    |
| **[[Document-oriented database]]** | Documents (JSON/BSON)             | Schemaless, queryable on value, horizontal scaling.                   | **[[MongoDB]]**  |
| **[[Column-oriented database]]**   | Key and multiple columns per row  | Fast access to specific columns, good for analytics/BI/Event logging. | Apache Cassandra |
| **[[Graph Database]]**             | Nodes, Relationships, Paths       | Highly related data, vertical scaling, ACID compliant.                | **[[Neo4j]]**    |