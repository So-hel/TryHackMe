# 🌐 Putting It All Together — TryHackMe Notes

> **Author:** Sohel  
> **Room:** [Putting It All Together](https://tryhackme.com/room/puttingitalltogether) — TryHackMe Pre-Security Learning Path  
> **Status:** ✅ Completed

---

## 📌 Table of Contents

- [Introduction]
- [Task 2 — Other Components]
- [Task 3 — How Web Servers Work]
- [Task 4 — Quiz (Website Request Flow)]
- [Conclusion]

---

## Introduction

This room simulates the **end-to-end process** that occurs when a user requests a website. It connects concepts from DNS resolution and caching through to firewalls, load balancers, and the full backend application stack.

---

## Task 2 — Other Components

### 🔹 Key Web Components

| Component | Role |
|-----------|------|
| **CDN** (Content Delivery Network) | Hosts static files across distributed servers to reduce latency |
| **Load Balancer** | Distributes traffic across multiple backend servers |
| **WAF** (Web Application Firewall) | Filters malicious HTTP/HTTPS requests before they reach the app |

### 🔹 CDN

A **CDN** hosts copies of static files (images, scripts, stylesheets) across geographically distributed servers. Serving assets from a nearby CDN node reduces latency and load on the origin server.

### 🔹 Load Balancer — Health Checks

Load balancers periodically run **health checks** (HTTP, TCP, or custom) against backend hosts to confirm they are responsive. If a host fails, the load balancer stops sending it traffic until it recovers.

### 🔹 WAF

A **WAF** inspects incoming requests and filters out malicious patterns such as:
- 💉 SQL Injection
- 🔀 Cross-Site Scripting (XSS)
- 🚨 Known attack signatures

---

### ✅ Task 2 Answers

| Question | Answer |
|----------|--------|
| What can be used to host static files and speed up a client's visit? | `CDN` |
| What does a load balancer perform to check if a host is alive? | `Health check` |
| What can be used to help against the hacking of a website? | `WAF` |

---

## Task 3 — How Web Servers Work

### 🔹 Virtual Hosts

**Virtual hosts** allow a single web server (one IP and port) to serve **multiple domain names** by routing requests based on the `Host` header — enabling efficient multi-tenancy on the same server.

### 🔹 Static vs Dynamic Content

| Type | Description |
|------|-------------|
| **Static** | Files that don't change unless updated on disk (e.g. images, HTML files) |
| **Dynamic** | Generated on demand based on user input, DB queries, or app logic |

### 🔹 Backend Code Visibility

Backend code (server-side scripts, database queries, application logic) runs **on the server** and is never sent to the client. The client only receives the rendered output — HTML, CSS, JS, or JSON.

---

### ✅ Task 3 Answers

| Question | Answer |
|----------|--------|
| What does web server software use to host multiple sites? | `Virtual Hosts` |
| What is the name for the type of content that can change? | `Dynamic` |
| Does the client see the backend code? | `Nay` |

---

## Task 4 — Quiz (Website Request Flow)

The correct order of how a request to a website works:

```
1.  Request a website in your browser
        ↓
2.  Check local cache for the IP address
        ↓
3.  Check your recursive DNS server for the address
        ↓
4.  Query a root server to find the authoritative DNS server
        ↓
5.  The authoritative DNS server provides the IP address
        ↓
6.  The request passes through a WAF
        ↓
7.  The request passes through a Load Balancer
        ↓
8.  The browser connects to the web server on port 80 or 443
        ↓
9.  The web server receives the GET request
        ↓
10. The web application communicates with the database
        ↓
11. Your browser renders the HTML into a viewable website
```

### 🔹 Step-by-Step Breakdown

| Step | Component | What Happens |
|------|-----------|-------------|
| 1 | Browser | User types a URL; browser prepares to fetch the resource |
| 2 | Local Cache | OS/browser checks if a DNS record is already cached |
| 3 | Recursive DNS | If cache misses, the client queries the configured DNS resolver |
| 4 | Root Server | Recursive resolver queries DNS hierarchy to find the authoritative nameserver |
| 5 | Authoritative DNS | Returns the final IP address for the requested domain |
| 6 | WAF | Filters malicious HTTP(S) requests before they reach the app |
| 7 | Load Balancer | Distributes traffic and routes to a healthy backend server |
| 8 | TCP/TLS | Browser establishes connection to the server on port 80 or 443 |
| 9 | Web Server | Accepts the GET request and routes it to the correct virtual host |
| 10 | Database | Application queries the DB for dynamic content if needed |
| 11 | Browser | Parses and renders HTML/CSS/JS into the final visible page |

---

### ✅ Task 4 Answers

| Question | Answer |
|----------|--------|
| Flag from ordering the request flow correctly | `THM{YOU_GOT_THE_ORDER}` |

---

## Conclusion

This room reinforces that delivering a website is a **coordinated multi-layer process**:

- 🔍 **Naming & Discovery** — DNS and caching ensure the browser finds the correct server
- 🛡️ **Edge Components** — CDN, WAF, and Load Balancer optimize performance, security, and availability
- ⚙️ **Server-Side** — Virtual hosts, web server, application, and database produce the actual content
- 🖥️ **Client-Side Rendering** — The browser turns HTTP responses into the final user-facing webpage

Understanding this flow helps diagnose performance issues, reason about security controls, and design resilient web architectures.

---

> 📚 **Next Room:** Continue the Pre-Security path on [TryHackMe](https://tryhackme.com)!

---

*Notes by **Sohel** | TryHackMe Pre-Security Learning Path*
