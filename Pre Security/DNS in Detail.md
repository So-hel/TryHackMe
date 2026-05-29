# 🌐 DNS in Detail — TryHackMe Notes

> **Author:** Sohel  
> **Room:** [DNS in Detail](https://tryhackme.com/room/dnsindetail) — TryHackMe Pre-Security Learning Path  
> **Status:** ✅ Completed

---

## 📌 Table of Contents

- [Task 1 — What is DNS?](#task-1--what-is-dns)
- [Task 2 — Domain Hierarchy](#task-2--domain-hierarchy)
- [Task 3 — Record Types](#task-3--record-types)
- [Task 4 — Making a Request](#task-4--making-a-request)
- [Task 5 — Practical](#task-5--practical)
- [Conclusion](#conclusion)

---

## Task 1 — What is DNS?

**DNS (Domain Name System)** is the system that translates human-readable domain names (like `tryhackme.com`) into IP addresses that computers use to communicate. Without DNS, you would need to remember the IP address of every website you visit.

> Think of DNS as the phonebook of the Internet — you look up a name and get back a number.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What does DNS stand for? | `Domain Name System` |

---

## Task 2 — Domain Hierarchy

DNS uses a hierarchical structure to organise domain names. From right to left, a domain is made up of:

```
subdomain . second-level-domain . top-level-domain
   blog   .      tryhackme      .       com
```

### 🏗️ Domain Levels Explained

| Level | Example | Description |
|-------|---------|-------------|
| **TLD** (Top-Level Domain) | `.com`, `.org`, `.co.uk` | The rightmost part of a domain |
| **Second-Level Domain** | `tryhackme` | The domain name registered by the owner |
| **Subdomain** | `blog`, `shop` | Created by the domain owner; sits to the left |

### 🌍 Types of TLD

| Type | Full Name | Example | Description |
|------|-----------|---------|-------------|
| **gTLD** | Generic Top-Level Domain | `.com`, `.org`, `.edu` | Indicates the purpose of the domain |
| **ccTLD** | Country Code Top-Level Domain | `.co.uk`, `.ca`, `.de` | Used for geographical regions or countries |

### 📏 Limits & Rules

- Maximum length of a **subdomain**: `63` characters
- Maximum length of a **full domain name**: `253` characters
- Subdomains **cannot** contain underscores (`_`) — only letters, numbers, and hyphens are allowed

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the maximum length of a subdomain? | `63` |
| Which of the following characters cannot be used in a subdomain ( 3 b _ - )? | `_` |
| What is the maximum length of a domain name? | `253` |
| What type of TLD is .co.uk? | `ccTLD` |

---

## Task 3 — Record Types

DNS isn't just for websites — it stores several types of records, each serving a different purpose.

### 📋 Common DNS Record Types

| Record Type | Purpose | Example |
|-------------|---------|---------|
| **A** | Maps a domain to an **IPv4** address | `10.10.10.10` |
| **AAAA** | Maps a domain to an **IPv6** address | `2606:4700::6810:84e5` |
| **CNAME** | Maps a domain to **another domain name** (alias) | `shop.website.thm → shops.myshopify.com` |
| **MX** | Specifies the **mail server** for a domain | `mail.website.thm` |
| **TXT** | Stores **free-form text** data (used for verification, SPF, etc.) | `THM{...}` |

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What type of record would be used to advise where to send email? | `MX` |
| What type of record handles IPv6 addresses? | `AAAA` |

---

## Task 4 — Making a Request

When you type a domain into your browser, a DNS lookup happens behind the scenes through several stages:

### 🔄 DNS Resolution Process

```
Your Device
    |
    ↓ Check local cache → if found, use it
    |
    ↓ Query Recursive DNS Server (usually provided by your ISP)
    |
    ↓ Recursive server checks its cache → if not found:
    |
    ↓ Query Root DNS Server → points to correct TLD server
    |
    ↓ Query TLD Server → points to Authoritative Name Server
    |
    ↓ Query Authoritative Name Server → returns the actual record
    |
    ↓ Result returned to your device & cached for TTL duration
```

### 🗂️ Key DNS Server Types

| Server Type | Role |
|-------------|------|
| **Recursive DNS Server** | First stop after your device; usually provided by your ISP; queries other servers on your behalf |
| **Root DNS Server** | Top of the DNS hierarchy; directs queries to the correct TLD server |
| **TLD Server** | Handles queries for a specific TLD (e.g. `.com`); points to the authoritative server |
| **Authoritative Name Server** | Holds all the DNS records for a domain; gives the final answer |

### ⏱️ TTL (Time To Live)

**TTL** is a value in a DNS record that specifies how long (in seconds) the record should be **cached** before a fresh lookup is required. A lower TTL means changes propagate faster; a higher TTL reduces DNS query load.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What field specifies how long a DNS record should be cached for? | `TTL` |
| What type of DNS Server is usually provided by your ISP? | `Recursive` |
| What type of server holds all the records for a domain? | `Authoritative` |

---

## Task 5 — Practical

The practical provides an interactive DNS lookup tool where you can change the record type and query a test domain (`website.thm`) to find specific record values.

### 🔍 Lookup Results for `website.thm`

| Query | Record Type | Result |
|-------|-------------|--------|
| `shop.website.thm` | CNAME | `shops.myshopify.com` |
| `website.thm` | TXT | `THM{7012BBA60997F35A9516C2E16D2944FF}` |
| `website.thm` | MX (priority) | `30` |
| `www.website.thm` | A | `10.10.10.10` |

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the CNAME of shop.website.thm? | `shops.myshopify.com` |
| What is the value of the TXT record of website.thm? | `THM{7012BBA60997F35A9516C2E16D2944FF}` |
| What is the numerical priority value for the MX record? | `30` |
| What is the IP address for the A record of www.website.thm? | `10.10.10.10` |

---

## Conclusion

This room covers how the Domain Name System works from top to bottom:

- 🌐 **DNS** — translates domain names into IP addresses so devices can communicate
- 🏗️ **Domain Hierarchy** — structured as Subdomain → Second-Level Domain → TLD; ccTLD for countries, gTLD for general use
- 📋 **Record Types** — A (IPv4), AAAA (IPv6), CNAME (alias), MX (email), TXT (text/verification)
- 🔄 **DNS Resolution** — Recursive → Root → TLD → Authoritative server chain
- ⏱️ **TTL** — controls how long a DNS record is cached before a fresh lookup is needed

---

*Notes by **Sohel** | TryHackMe Pre-Security Learning Path*
