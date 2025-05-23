# Distributed Systems: Building Blocks

We’ll discuss the following building blocks in detail, topologically ordered so that dependencies appear in sequence.


## 📘 Plan

1. [Domain Name System (DNS)](#1-domain-name-system-dns)
2. [Load Balancers](#2-load-balancers)
3. [Databases](#3-databases)
4. [Key-Value Store](#4-key-value-store)
5. [Content Delivery Network (CDN)](#5-content-delivery-network-cdn)
6. [Sequencer](#6-sequencer)
7. [Service Monitoring](#7-service-monitoring)
8. [Distributed Caching](#8-distributed-caching)
9. [Distributed Messaging Queue](#9-distributed-messaging-queue)
10. [Publish-Subscribe System](#10-publish-subscribe-system)
11. [Rate Limiter](#11-rate-limiter)
12. [Blob Store](#12-blob-store)
13. [Distributed Search](#13-distributed-search)
14. [Distributed Logging](#14-distributed-logging)
15. [Distributed Task Scheduling](#15-distributed-task-scheduling)
16. [Sharded Counters](#16-sharded-counters)

---

## 1. Domain Name System (DNS)

Focuses on designing hierarchical and distributed naming systems for computers connected to the Internet using various protocols.

---

## 2. Load Balancers

Explores the design of load balancers that fairly distribute incoming client requests among a pool of available servers. They also help bypass failed servers and reduce load.

---

## 3. Databases

Covers the fundamentals of storing, retrieving, modifying, and deleting data in distributed environments. Topics include:
- Database types
- Replication
- Partitioning
- Analysis of distributed databases

---

## 4. Key-Value Store

A non-relational database storing data as key-value pairs. This section includes:
- Scalability
- Durability
- Configurability

---

## 5. Content Delivery Network (CDN)

Designs a CDN to cache and deliver viral content (videos, images, web pages) closer to users, reducing latency and load on data centers.

---

## 6. Sequencer

Focuses on designing a unique ID generator that maintains causality. Includes three approaches for generating unique IDs.

---

## 7. Service Monitoring

Monitoring systems are critical for analyzing distributed systems and providing early warnings. This section covers:
- Server-side monitoring
- Client-side error monitoring

---

## 8. Distributed Caching

Designs a distributed caching system involving multiple coordinated cache servers for storing frequently accessed data.

---

## 9. Distributed Messaging Queue

Explains the design of queues used between producers and consumers to:
- Decouple interaction
- Achieve independent scalability
- Enhance reliability

---

## 10. Publish-Subscribe System

Covers asynchronous service-to-service communication methods used in:
- Microservices architectures
- Serverless systems
- Data pipelines

---

## 11. Rate Limiter

Designs a system to throttle incoming requests based on predefined limits, acting as a defensive layer against misuse or overload.

---

## 12. Blob Store

Provides a storage solution for unstructured data such as:
- Multimedia files
- Binary executables

---

## 13. Distributed Search

Covers three components of a search system:
- Crawl
- Index
- Search

Returns relevant results to user queries in near real-time.

---

## 14. Distributed Logging

Designs a scalable, reliable system for efficient event logging in distributed environments.

---

## 15. Distributed Task Scheduling

Designs a system that:
- Mediates between tasks and resources
- Intelligently allocates resources
- Supports asynchronous background processing

---

## 16. Sharded Counters

Demonstrates an efficient system for high-concurrency counting, such as tracking likes on a viral post.

---
