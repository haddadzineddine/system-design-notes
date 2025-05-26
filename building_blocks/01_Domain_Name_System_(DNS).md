
## Domain Name System (DNS)

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
