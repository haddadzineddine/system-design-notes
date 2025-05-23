# Distributed Systems

## 📘 Plan

1. [System Design Concepts](#1-system-design-concepts)
2. [Domain Name System (DNS)](#2-domain-name-system-dns)
3. [Load Balancers](#3-load-balancers)
4. [Databases](#4-databases)
5. [Key-Value Store](#5-key-value-store)
6. [Content Delivery Network (CDN)](#6-content-delivery-network-cdn)
7. [Sequencer](#7-sequencer)
8. [Service Monitoring](#8-service-monitoring)
9. [Distributed Caching](#9-distributed-caching)
10. [Distributed Messaging Queue](#10-distributed-messaging-queue)
11. [Publish-Subscribe System](#11-publish-subscribe-system)
12. [Rate Limiter](#12-rate-limiter)
13. [Blob Store](#13-blob-store)
14. [Distributed Search](#14-distributed-search)
15. [Distributed Logging](#15-distributed-logging)
16. [Distributed Task Scheduling](#16-distributed-task-scheduling)
17. [Sharded Counters](#17-sharded-counters)

## 1. System Design Concepts
- Scalability
- Availability
- CAP Theorem
- ACID Transactions
- Consistent Hashing
- Rate Limiting
- Fault Tolerance

## 2. Domain Name System (DNS)

Focuses on designing hierarchical and distributed naming systems for computers connected to the Internet using various protocols.

---

## 3. Load Balancers

Explores the design of load balancers that fairly distribute incoming client requests among a pool of available servers. They also help bypass failed servers and reduce load.

---

## 4. Databases

Covers the fundamentals of storing, retrieving, modifying, and deleting data in distributed environments. Topics include:
- Database types
- Replication
- Partitioning
- Analysis of distributed databases

---

## 5. Key-Value Store

A non-relational database storing data as key-value pairs. This section includes:
- Scalability
- Durability
- Configurability

---

## 6. Content Delivery Network (CDN)

Designs a CDN to cache and deliver viral content (videos, images, web pages) closer to users, reducing latency and load on data centers.

---

## 7. Sequencer

Focuses on designing a unique ID generator that maintains causality. Includes three approaches for generating unique IDs.

---

## 8. Service Monitoring

Monitoring systems are critical for analyzing distributed systems and providing early warnings. This section covers:
- Server-side monitoring
- Client-side error monitoring

---

## 9. Distributed Caching

Designs a distributed caching system involving multiple coordinated cache servers for storing frequently accessed data.

---

## 10. Distributed Messaging Queue

Explains the design of queues used between producers and consumers to:
- Decouple interaction
- Achieve independent scalability
- Enhance reliability

---

## 11. Publish-Subscribe System

Covers asynchronous service-to-service communication methods used in:
- Microservices architectures
- Serverless systems
- Data pipelines

---

## 12. Rate Limiter

Designs a system to throttle incoming requests based on predefined limits, acting as a defensive layer against misuse or overload.

---

## 13. Blob Store

Provides a storage solution for unstructured data such as:
- Multimedia files
- Binary executables

---

## 14. Distributed Search

Covers three components of a search system:
- Crawl
- Index
- Search

Returns relevant results to user queries in near real-time.

---

## 15. Distributed Logging

Designs a scalable, reliable system for efficient event logging in distributed environments.

---

## 16. Distributed Task Scheduling

Designs a system that:
- Mediates between tasks and resources
- Intelligently allocates resources
- Supports asynchronous background processing

---

## 17. Sharded Counters

Demonstrates an efficient system for high-concurrency counting, such as tracking likes on a viral post.

---
