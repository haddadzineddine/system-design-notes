# ⚙️ Distributed Systems Notes (With the help of AI)

A curated guide to the core components and design principles behind large-scale, reliable, and scalable distributed systems.

---

## 📚 Plan

1. [Building Blocks](#1-building-blocks)  
   - [1.1 Domain Name System (DNS)](building_blocks/01_Domain_Name_System_(DNS).md)  
   - [1.2 Load Balancers](building_blocks/02_Load_Balancers.md)  
   - [1.3 Databases](building_blocks/03_Databases.md)  
   - [1.4 Key-Value Store](building_blocks/04_Key-Value_Store.md)  
   - [1.5 Content Delivery Network (CDN)](building_blocks/05_Content_Delivery_Network_(CDN).md)  
   - [1.6 Sequencer](building_blocks/06_Sequencer.md)  
   - [1.7 Service Monitoring](building_blocks/07_Service_Monitoring.md)  
   - [1.8 Distributed Caching](building_blocks/08_Distributed_Caching.md)  
   - [1.9 Distributed Messaging Queue](building_blocks/09_Distributed_Messaging_Queue.md)  
   - [1.10 Publish-Subscribe System](building_blocks/10_Publish-Subscribe_System.md)  
   - [1.11 Rate Limiter](building_blocks/11_Rate_Limiter.md)  
   - [1.12 Blob Store](building_blocks/12_Blob_Store.md)  
   - [1.13 Distributed Search](building_blocks/13_Distributed_Search.md)  
   - [1.14 Distributed Logging](building_blocks/14_Distributed_Logging.md)  
   - [1.15 Distributed Task Scheduling](building_blocks/15_Distributed_Task_Scheduling.md)  
   - [1.16 Sharded Counters](building_blocks/16_Sharded_Counters.md)



## 1. Building Blocks

A collection of foundational components used in designing distributed systems. Each topic explores design principles, trade-offs, and typical use cases.

- **Domain Name System (DNS)** – Maps domain names to IP addresses for service discovery.
- **Load Balancers** – Distribute traffic across servers to ensure high availability.
- **Databases** – Store and manage structured data with consistency guarantees.
- **Key-Value Store** – Fast storage system for simple key-value data access.
- **Content Delivery Network (CDN)** – Serves static content from edge locations to reduce latency.
- **Sequencer** – Provides a consistent global order of events or operations.
- **Service Monitoring** – Observes system health through metrics and alerts.
- **Distributed Caching** – Stores frequently accessed data in-memory across nodes.
- **Distributed Messaging Queue** – Enables asynchronous communication between services.
- **Publish-Subscribe System** – Allows message broadcasting to multiple subscribers.
- **Rate Limiter** – Restricts request rate to protect systems from overload.
- **Blob Store** – Stores large binary files like images, videos, or backups.
- **Distributed Search** – Scalable search over large datasets using distributed indexing.
- **Distributed Logging** – Centralizes logs from multiple sources for analysis.
- **Distributed Task Scheduling** – Manages background jobs across multiple nodes.
- **Sharded Counters** – Splits counting logic to scale under high load.
