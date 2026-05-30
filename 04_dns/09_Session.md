# DNS (Domain Name System) - Revision Notes

## 📑 Index

1. [What is DNS?](#1-what-is-dns)
2. [DNS Resolution Process](#2-dns-resolution-process)
3. [Root Servers](#3-root-servers)
4. [Top Level Domains (TLD)](#4-top-level-domains-tld)
5. [Domain Registrars](#5-domain-registrars)
6. [How to Buy a Domain](#6-how-to-buy-a-domain)
7. [Nameservers (NS Records)](#7-nameservers-ns-records)
8. [DNS Records](#8-dns-records)
9. [A Record](#9-a-record)
10. [TTL (Time To Live)](#10-ttl-time-to-live)
11. [Hosted Zone in AWS](#11-hosted-zone-in-aws)
12. [Important Interview Questions](#12-important-interview-questions)

---

# 1. What is DNS?

DNS (Domain Name System) is the internet's phone book.

Humans remember domain names:

* facebook.com
* google.com
* joindevops.com

Computers communicate using IP addresses:

* 157.240.22.35
* 142.250.183.14

DNS translates a domain name into an IP address.

### DNS Resolver

A DNS Resolver is responsible for finding the IP address of a domain.

Example:

```text
google.com → DNS Resolver → 142.250.183.14
```

---

# 2. DNS Resolution Process

When you open a website in a browser:

```text
Browser
   ↓
Browser Cache
   ↓
OS Cache
   ↓
ISP DNS Resolver Cache
   ↓
Root Server
   ↓
TLD Server
   ↓
Domain Registrar / Authoritative Name Server
   ↓
A Record
   ↓
IP Address Returned
```

Example:

```text
joindevops.com
       ↓
DNS Resolver
       ↓
Root Server
       ↓
.com TLD Server
       ↓
Name Server
       ↓
A Record
       ↓
167.89.87.23
```

The browser then connects to the returned IP address.

---

# 3. Root Servers

Root servers are the highest level in the DNS hierarchy.

### Key Points

* There are 13 logical root server clusters.
* Managed by different organizations around the world.
* Root servers know where every TLD server is located.
* Root servers do NOT store website IP addresses.

### Responsibilities

Root servers maintain information about:

* TLD locations
* TLD servers
* DNS hierarchy

Example:

```text
User asks for google.com

Root Server says:
"I don't know the IP,
but .com TLD server knows."
```

---

# 4. Top Level Domains (TLD)

TLD = Top Level Domain

It is the last portion of a domain name.

Examples:

```text
.com
.net
.org
.edu
.us
.uk
.in
.ai
.shop
.online
.co
```

### Examples

```text
google.com      → .com
amazon.in       → .in
university.edu  → .edu
```

### Country Based TLDs

```text
.in  → India
.uk  → United Kingdom
.us  → United States
.tv  → Tuvalu Government
```

Example:

```text
ivs.tv
```

Uses the `.tv` TLD which belongs to Tuvalu.

---

# 5. Domain Registrars

A Domain Registrar is a company authorized to sell domain names.

Examples:

* GoDaddy
* Hostinger
* Porkbun
* AWS Route53
* Google Cloud
* Azure

### Responsibilities

* Register domains
* Renew domains
* Manage DNS records
* Manage nameservers

Example:

```text
joindevops.com
```

May be purchased from:

* GoDaddy
* Hostinger
* Porkbun

The domain can later be transferred to another registrar.

---

# 6. How to Buy a Domain

Example:

```text
joindevops.com
```

### Step 1: Availability Check

Registrar checks with the TLD authority.

```text
Is joindevops.com available?
```

If yes, proceed.

### Step 2: Customer Information

Registrar collects:

* Name
* Company
* Address
* Phone Number
* Email Address
* Payment Information

### Step 3: Payment

After payment:

* Registrar updates TLD records.
* Ownership information is registered.

### Step 4: Configure DNS

Create DNS records such as:

```text
joindevops.com A 167.89.87.23
```

Now visitors can reach the server.

---

# 7. Nameservers (NS Records)

NS = Name Server

Nameservers are responsible for answering DNS queries for a domain.

### Purpose

They tell the internet:

```text
Who manages this domain?
Who provides the IP address?
```

Example:

```text
joindevops.com
      ↓
NS Records
      ↓
ns1.hostinger.com
ns2.hostinger.com
```

The nameserver contains all DNS records for the domain.

---

# 8. DNS Records

DNS stores different types of records.

Common records:

| Record Type | Purpose                           |
| ----------- | --------------------------------- |
| A           | Maps domain to IPv4 address       |
| AAAA        | Maps domain to IPv6 address       |
| CNAME       | Alias to another domain           |
| MX          | Mail Server                       |
| NS          | Name Servers                      |
| TXT         | Verification and security records |

---

# 9. A Record

A Record maps a domain name to an IPv4 address.

Example:

```text
joindevops.com → 167.89.87.23
```

DNS Entry:

```text
Type : A
Name : joindevops.com
Value: 167.89.87.23
```

When a user visits:

```text
https://joindevops.com
```

DNS returns:

```text
167.89.87.23
```

The browser connects to that server.

---

# 10. TTL (Time To Live)

TTL determines how long DNS information remains cached.

Example:

```text
TTL = 3600 seconds
```

Meaning:

```text
1 hour
```

DNS caches keep the record for one hour before checking again.

### During Migration

Before changing servers:

Reduce TTL.

Example:

```text
TTL = 1 second
```

or

```text
TTL = 60 seconds
```

Wait for propagation.

Make DNS changes.

After everything is working:

```text
TTL = 3600
```

or higher.

### Why?

Lower TTL:

* Faster updates
* Faster propagation

Higher TTL:

* Better performance
* Less DNS traffic

---

# 11. Hosted Zone in AWS

AWS Route53 uses Hosted Zones.

A Hosted Zone is a container for DNS records of a domain.

Example:

```text
Hosted Zone:
joindevops.com
```

Contains:

```text
A Record
CNAME Record
MX Record
TXT Record
NS Record
```

### Workflow

```text
Buy Domain
     ↓
Create Hosted Zone
     ↓
Create A Record
     ↓
Point Domain to Server IP
```

Example:

```text
joindevops.com
      ↓
A Record
      ↓
167.89.87.23
```

---

# 12. Important Interview Questions

### What is DNS?

DNS converts domain names into IP addresses.

---

### What is a DNS Resolver?

A DNS Resolver finds the IP address for a requested domain.

---

### What are Root Servers?

Root servers are the top level of the DNS hierarchy and know the location of TLD servers.

---

### What is a TLD?

TLD (Top Level Domain) is the last part of a domain name.

Examples:

```text
.com
.in
.org
.net
```

---

### What is a Domain Registrar?

A company authorized to register and manage domain names.

Examples:

```text
GoDaddy
Hostinger
Porkbun
AWS Route53
```

---

### What are Nameservers?

Nameservers manage DNS records and provide DNS answers for a domain.

---

### What is an A Record?

An A Record maps a domain name to an IPv4 address.

Example:

```text
joindevops.com → 167.89.87.23
```

---

### What is TTL?

TTL (Time To Live) defines how long DNS records stay in cache before refreshing.

---

## Quick Revision Diagram

```text
User opens google.com
          ↓
Browser Cache
          ↓
OS Cache
          ↓
ISP DNS Resolver
          ↓
Root Server
          ↓
.com TLD Server
          ↓
Authoritative Name Server
          ↓
A Record
          ↓
IP Address
          ↓
Website Opens
```

### Additional Notes (for exam/interviews)

* There are **13 logical root server names (A–M)**, but each is distributed globally using many physical servers via Anycast.
* **Root servers do not contact registrars directly during normal DNS lookups.** They point resolvers to the correct TLD servers.
* The **authoritative nameserver** (configured through NS records) ultimately provides the A record.
* **AWS Route 53 Hosted Zone** acts as the authoritative DNS database for your domain when Route 53 manages it.
* Typical domain purchase practice:

  * Temporary/testing domains → cheaper providers like Hostinger
  * Long-term production domains → choose a registrar based on reliability, pricing, and support (GoDaddy is one option, but not the only one).
