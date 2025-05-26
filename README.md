# ⚙️ Distributed Systems

A curated guide to the core components and design principles behind large-scale, reliable, and scalable distributed systems.

---

## 📚 Plan

1. [Building Blocks](#1-building-blocks)  
   - [1.1 Domain Name System (DNS)](#11-domain-name-system-dns)  
   - [1.2 Load Balancers](#12-load-balancers)  
   - [1.3 Databases](#13-databases)  
   - [1.4 Key-Value Store](#14-key-value-store)  
   - [1.5 Content Delivery Network (CDN)](#15-content-delivery-network-cdn)  
   - [1.6 Sequencer](#16-sequencer)  
   - [1.7 Service Monitoring](#17-service-monitoring)  
   - [1.8 Distributed Caching](#18-distributed-caching)  
   - [1.9 Distributed Messaging Queue](#19-distributed-messaging-queue)  
   - [1.10 Publish-Subscribe System](#110-publish-subscribe-system)  
   - [1.11 Rate Limiter](#111-rate-limiter)  
   - [1.12 Blob Store](#112-blob-store)  
   - [1.13 Distributed Search](#113-distributed-search)  
   - [1.14 Distributed Logging](#114-distributed-logging)  
   - [1.15 Distributed Task Scheduling](#115-distributed-task-scheduling)  
   - [1.16 Sharded Counters](#116-sharded-counters)

---

## 1. Building Blocks

### 1.1 Domain Name System (DNS)

#### 1. Introduction

The Domain Name System (DNS) is the Internet's equivalent of a phone book. It translates human-friendly domain names like `google.com` into machine-friendly IP addresses like `104.18.2.119`. Without DNS, we’d have to memorize IPs for every website we visit.

Just like you use a contact list instead of memorizing phone numbers, DNS allows users to navigate the web with names instead of numbers.

---

#### 2. DNS Hierarchy

DNS follows a hierarchical, distributed structure:

##### Root Domain (`.`)
- Top-level of the DNS hierarchy
- Represented as a trailing dot (`.`)
- Managed by 13 sets of root servers (A–M), replicated globally via anycast

##### Top-Level Domains (TLDs)
- Sit directly under the root
- Categories:
  - **Generic (gTLDs):** `.com`, `.org`, `.net`
  - **Sponsored TLDs:** `.edu`, `.gov`, `.mil`
  - **Country Code (ccTLDs):** `.uk`, `.fr`, `.dz`
- Managed by IANA/ICANN

##### Second-Level Domains (SLDs)
- Registered under TLDs (e.g., `example.com`)
- Often represent individuals, organizations, or brands

##### Subdomains
- Subdivisions of SLDs (e.g., `mail.example.com`)
- Used for apps, services, or departments

---

#### 3. DNS Components

##### 3.1 Domain Names & Zones

- A **domain name** is a human-readable identifier structured with labels (e.g., `www.example.com`).
- A **zone** is a portion of the domain namespace managed by an organization.
- **Delegation** assigns control of a subdomain using **NS records** to point to authoritative name servers.

##### 3.2 Name Servers

Different types of name servers serve specific roles:

- **Root Name Servers** – Respond to TLD queries (e.g., “Where is `.com`?”)
- **TLD Name Servers** – Handle queries for domains within a specific TLD
- **Authoritative Name Servers** – Provide final DNS answers and store zone files
- **Recursive Resolvers** – Query other servers on behalf of clients; cache results for performance

##### 3.3 Zone Files & DNS Records

A **zone file** contains DNS records mapping names to data.

###### Common DNS Records:

| Type   | Description                                |
|--------|--------------------------------------------|
| A      | Maps domain to IPv4 address                |
| AAAA   | Maps domain to IPv6 address                |
| CNAME  | Aliases one domain to another              |
| MX     | Defines mail servers for the domain        |
| NS     | Lists authoritative name servers           |
| SOA    | Contains zone metadata and contact info    |
| TXT    | Holds text data (e.g., SPF, domain keys)   |
| PTR    | Supports reverse DNS lookups               |
| SRV    | Defines service locations                  |

---

#### 4. DNS Record Use Cases

- **A / AAAA:** Connect users to a web server  
- **MX:** Direct email to mail servers  
- **CNAME:** Redirect `blog.example.com` → `example.tumblr.com`  
- **TXT:** Used for SPF, DKIM, domain verification  
- **NS:** Delegates authority for a zone  
- **PTR:** Maps an IP address back to a domain (reverse DNS)

---

#### 5. DNS as a Distributed System

DNS is globally distributed and designed for resilience and scalability.

##### Scalability
- Handles billions of queries daily
- Utilizes:
  - Recursive resolver caching
  - Anycast routing for root and TLD servers
  - Delegated zones to divide responsibility

##### Reliability
- Redundant infrastructure:
  - Multiple name servers per zone
  - Global anycast networks
  - Failover and monitoring systems

##### Consistency
- **TTL (Time-To-Live):** Controls cache duration
- **Zone Transfers (AXFR/IXFR):** Sync between primary and secondary servers
- **DNSSEC:** Adds cryptographic integrity to DNS responses

---

#### 6. How DNS Works (Step-by-Step)

##### 6.1 Resolution Flow: `www.google.com`

1. **Browser Cache** – Checks for cached IP  
2. **OS Cache** – Checks local resolver cache  
3. **Recursive Resolver** – Queries root if no cache  
4. **Root Server** – Responds with TLD server info (`.com`)  
5. **TLD Server** – Provides authoritative server for `google.com`  
6. **Authoritative Server** – Returns A/AAAA record for `www.google.com`  
7. **Caching** – Result cached at resolver, OS, and browser  
8. **HTTP(S) Request** – Browser connects to IP and requests content

---

##### 6.5 DNS Propagation

**Definition:**  
The time it takes for DNS changes to be reflected across the Internet.

**Why It Happens:**  
Because DNS relies on distributed caches that respect TTLs.

**Propagation Process:**
1. Update DNS record with provider  
2. Authoritative servers reflect changes  
3. Cached records expire across recursive resolvers  
4. New data gradually becomes visible globally

**How to Check:**
- Use tools like `dig`, `nslookup`, or online DNS checkers

---

#### 7. Further Reading

- [What is DNS? (Cloudflare)](https://www.cloudflare.com/learning/dns/what-is-dns/)
- [Under the Hood of a Simple DNS Server](https://github.com/tonybaloney/simple-dns-server)
- [What Happens When You Type www.google.com?](https://github.com/alex/what-happens-when)
- [Introduction to the Domain Name System (ICANN)](https://www.icann.org/resources/pages/welcome-2012-02-25-en)

---

### 1.2 Load Balancers

Load balancers distribute incoming client requests evenly across multiple servers, improving availability, fault tolerance, and scalability.

#### Key Functions:
- **Request Distribution:** Balances load fairly among servers to prevent overload.
- **Health Checks:** Detects and bypasses failed or unhealthy servers.
- **Session Persistence:** Ensures requests from the same client go to the same server when needed.
- **SSL Termination:** Handles TLS/SSL encryption to offload processing from backend servers.

#### Load Balancing Algorithms:
- **Round Robin:** Requests sent sequentially to each server.
- **Least Connections:** Routes requests to the server with the fewest active connections.
- **IP Hash:** Uses client IP address to consistently route requests to the same server.
- **Weighted:** Distributes requests based on server capacity or priority.

---

### 1.3 Databases

Databases are fundamental for storing, retrieving, and modifying data reliably in distributed systems.

#### Core Concepts:
- **Database Types:** Relational (SQL) vs Non-relational (NoSQL)
- **Replication:** Copies data across servers for fault tolerance and read scaling.
- **Partitioning (Sharding):** Splits data across multiple nodes for write scaling.
- **Consistency Models:** Balancing between strong and eventual consistency depending on use case.

---

### 1.4 Key-Value Store

A non-relational database optimized for storing data as simple key-value pairs.

#### Characteristics:
- **High Scalability:** Easily distributed across many nodes.
- **Durability:** Ensures data persistence and recovery.
- **Configurability:** Flexible consistency and replication options.
  
Common use cases include caching, session management, and real-time analytics.

---

### 1.5 Content Delivery Network (CDN)

CDNs cache and serve content (like videos, images, and web pages) from servers close to users to reduce latency and bandwidth use.

#### Design Highlights:
- **Edge Caching:** Stores content geographically closer to end-users.
- **Cache Invalidation:** Mechanisms to refresh stale content.
- **Load Distribution:** Balances traffic across edge servers.
- **DDoS Mitigation:** Protects origin servers by absorbing traffic at edges.

---

### 1.6 Sequencer

A sequencer generates unique, ordered IDs in distributed systems, maintaining causality and avoiding collisions.

#### Approaches:
- **Centralized Sequencer:** Single authority issues IDs.
- **Timestamp-based IDs:** Use time components (e.g., Twitter Snowflake).
- **UUIDs:** Universally unique but not necessarily ordered.

---

### 1.7 Service Monitoring

Monitoring systems collect metrics and logs to analyze system health and detect failures early.

#### Components:
- **Server-side Monitoring:** CPU, memory, latency, error rates.
- **Client-side Monitoring:** User experience and frontend errors.
- **Alerting Systems:** Notify teams of anomalies.

---

Let me know if you'd like me to keep going with the rest, or want a full consolidated file for your README!
