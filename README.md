# System Design Notes (Zero to Hero)

This repo contains my structured notes on System Design, covering basics to advanced concepts.  

---

## Table of Contents
1. [Client-Server Model](#1-client-server-model)  
2. [Scalability](#2-scalability)  
3. [Latency vs Throughput](#3-latency-vs-throughput)  
4. [Load Balancing](#4-load-balancing)  
5. [Caching](#5-caching)  
6. [DNS & CDN](#6-dns--cdn)  
7. [Databases](#7-databases)  
8. [Message Queues](#8-message-queues)  
9. [API Design & Storage](#9-api-design--storage)  
10. [Microservices vs Monolithic](#10-microservices-vs-monolithic)  
11. [WebSockets](#11-websockets)  
12. [Sharding](#12-sharding)  
13. [CAP Theorem](#13-cap-theorem)  
14. [Consistency Models](#14-consistency-models)  

---

## 1. Client-Server Model
- A fundamental architecture where clients (users) request services and servers provide responses.  
- Examples:
  - Browser (client) requests a webpage from a web server.
  - Mobile app calls backend APIs.  

Advantages: Simple and widely used.  
Disadvantage: Single server may become a bottleneck.  

---

## 2. Scalability
- Ability of a system to handle growth in users or data.  

Types:  
- Vertical Scaling (Scale Up): Add more CPU/RAM to a single machine.  
- Horizontal Scaling (Scale Out): Add more servers.  

Most modern systems prefer horizontal scaling.  

---

## 3. Latency vs Throughput
- Latency: Time taken for a request to get a response (measured in ms).  
- Throughput: Number of requests handled per second.  

Goal: Low latency and high throughput.  

Example:  
- WhatsApp message delivery → requires low latency.  
- YouTube video streaming → requires high throughput.  

---

## 4. Load Balancing
- A traffic distributor that spreads requests across multiple servers.  
- Benefits:
  - Prevents server overload
  - Improves availability
  - Reduces response time  

Examples: Nginx, HAProxy, AWS Elastic Load Balancer.  

---

## 5. Caching
- Storing frequently used data in fast memory.  

Levels of Caching:  
1. Browser Cache: Local storage of static files.  
2. Application Cache: Redis, Memcached.  
3. CDN Cache: Content stored closer to users.  

Advantages: Improves performance.  
Challenge: Cache invalidation is difficult.  

---

## 6. DNS & CDN
- DNS (Domain Name System): Converts domain names to IP addresses.  
  - Example: `google.com → 142.250.182.14`.  

- CDN (Content Delivery Network): Globally distributed servers delivering cached content near users.  
  - Examples: Cloudflare, Akamai.  

Advantage: Faster content delivery.  

---

## 7. Databases
### SQL (Relational Databases)
- Structured, strict schema.  
- Examples: MySQL, PostgreSQL.  

### NoSQL (Non-Relational Databases)
- Flexible, scalable.  
- Types:  
  - Document: MongoDB  
  - Key-Value: Redis  
  - Column: Cassandra  
  - Graph: Neo4j  

Trade-off: SQL = Strong consistency, NoSQL = Better scalability.  

---

## 8. Message Queues
- A buffer for communication between services.  
- Producers push data → Queue → Consumers process it.  

Examples: Kafka, RabbitMQ, AWS SQS.  

Use cases: Asynchronous processing, decoupling services, handling spikes in traffic.  

---

## 9. API Design & Storage
- APIs are the communication bridge between client and server.  
- Types:
  - REST (widely used, simple)
  - GraphQL (flexible queries)
  - gRPC (high-performance, binary-based)  

Storage Design Considerations:  
- Relational vs Non-Relational DB  
- File storage vs Object storage (AWS S3, Google Cloud Storage)  

---

## 10. Microservices vs Monolithic
### Monolithic Architecture
- Single codebase, tightly coupled.  
- Easier to start, harder to scale.  

### Microservices Architecture
- System broken into smaller independent services.  
- Advantages: Scalability, independent deployment.  
- Challenges: Complex communication, monitoring, debugging.  

---

## 11. WebSockets
- Protocol for **real-time, two-way communication** between client and server.  
- Examples:
  - Chat applications
  - Live sports updates
  - Online multiplayer games  

Difference from HTTP: HTTP is request-response, WebSockets are persistent connections.  

---

## 12. Sharding
- Splitting a database into smaller pieces (shards) for better scalability.  
- Each shard handles a subset of data.  

Example: Users A–M stored in Shard 1, N–Z stored in Shard 2.  

Advantage: Distributes load, supports very large datasets.  
Disadvantage: Complex to implement and maintain.  

---

## 13. CAP Theorem
In distributed systems, you can only guarantee two out of three:  
1. Consistency – Every read gets the latest data.  
2. Availability – Every request gets a response, even if outdated.  
3. Partition Tolerance – System works even if communication between nodes fails.  

Examples:  
- CP Systems: HBase, MongoDB (prioritize consistency + partition tolerance).  
- AP Systems: DynamoDB, Cassandra (prioritize availability + partition tolerance).  

---

## 14. Consistency Models
When data is replicated, different models define how consistent reads are.  

- Strong Consistency: Reads always return the latest write. Example: Banking system.  
- Weak Consistency: Reads may return stale data. Example: Chat "last seen" updates.  
- Eventual Consistency: Data becomes consistent over time. Example: Social media likes.  

---