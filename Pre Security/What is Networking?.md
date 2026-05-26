# 🌐 What is Networking? — TryHackMe Notes

> **Author:** Sohel  
> **Room:** [What is Networking?](https://tryhackme.com/room/whatisnetworking) — TryHackMe Pre-Security Learning Path  
> **Status:** ✅ Completed

---

## 📌 Table of Contents

- [Task 1 — What is Networking?]
- [Task 2 — What is the Internet?]
- [Task 3 — Identifying Devices on a Network]
- [Task 4 — Ping (ICMP)]
- [Conclusion]

---

## Task 1 — What is Networking?

In simple terms, **networks are connections**. Just like a group of friends connected by shared interests, networks exist in all walks of life:

- 🚌 A city's public transportation system
- ⚡ National power grids
- 📮 Postal systems
- 💻 Computing devices

In computing, a network can be formed by anywhere from **2 devices to billions** — phones, laptops, security cameras, traffic lights, and more.


### ✅ Q1: What is the key term for devices that are connected?

**Answer:** `Network`

---

## Task 2 — What is the Internet?

The Internet is one **giant network** made up of many smaller networks. It was first conceived through the **ARPANET project in the late 1960s**, funded by the United States Defence Department.

In **1989**, **Tim Berners-Lee** invented the World Wide Web (WWW), transforming the Internet into a place for storing and sharing information.

Networks are of two types:
| Type | Description |
|------|-------------|
| **Private Network** | Small, local networks (e.g., home/office) |
| **Public Network** | The Internet — connects private networks together |


### ✅ Q1: Who invented the World Wide Web?

**Answer:** `Tim Berners-Lee`

---

## Task 3 — Identifying Devices on a Network

Devices on a network are identified using **two methods**, similar to how humans have a name and fingerprints:

| Identifier | Description |
|-----------|-------------|
| **IP Address** | Can change (like a name) |
| **MAC Address** | Permanent, tied to hardware (like a fingerprint) |

---

### 🔹 IP Addresses

An **IP address (Internet Protocol)** is a set of numbers divided into **four octets**, used to identify a device on a network.

```
Example: 192.168.1.77
```

Devices can have:
- **Private IP** — used within a local network
- **Public IP** — assigned by your ISP, used on the Internet

| Device Name | IP Address | Type |
|-------------|-----------|------|
| DESKTOP-KJE57FD | 192.168.1.77 | Private |
| DESKTOP-KJE57FD | 86.157.52.21 | Public |
| CMNatic-PC | 192.168.1.74 | Private |
| CMNatic-PC | 86.157.52.21 | Public |

#### IPv4 vs IPv6

| Version | Address Space |
|---------|--------------|
| IPv4 | 2³² (~4.29 billion addresses) |
| IPv6 | 2¹²⁸ (~340 trillion+ addresses) |

IPv6 was introduced to solve the **shortage of IPv4 addresses** as more devices connect to the Internet.


---

### 🔹 MAC Addresses

A **MAC (Media Access Control)** address is a **12-character hexadecimal number** assigned to a device's network interface at the factory.

```
Example: a4:c3:f0:85:ac:2d
```

- First 6 characters → Company that made the interface
- Last 6 characters → Unique device identifier

> ⚠️ **MAC Spoofing:** MAC addresses can be faked ("spoofed") to impersonate another device on a network — a common technique used to bypass MAC-based access controls.

---

### ✅ Task 3 Answers

| Question | Answer |
|----------|--------|
| What does "IP" stand for? | `Internet Protocol` |
| What is each section of an IP address called? | `Octet` |
| How many sections does an IP address have? | `4` |
| What does "MAC" stand for? | `Media Access Control` |
| Flag from the MAC spoofing lab? | `THM{YOU_GOT_ON_TRYHACKME}` |

---

## Task 4 — Ping (ICMP)

**Ping** is one of the most fundamental network tools. It uses **ICMP (Internet Control Message Protocol)** packets to test connectivity between devices.

```bash
# Basic ping syntax
ping <IP address>

# Example
ping 10.10.10.10

# Ping with a set count (Linux)
ping -c 4 8.8.8.8
```

- Sends an **ICMP echo** packet to the target
- Target responds with an **ICMP echo reply**
- The time taken is measured to determine connection speed and reliability


### ✅ Task 4 Answers

| Question | Answer |
|----------|--------|
| What protocol does ping use? | `ICMP` |
| What is the syntax to ping 10.10.10.10? | `ping 10.10.10.10` |
| Flag from pinging 8.8.8.8? | `THM{I_PINGED_THE_SERVER}` |

---

## Conclusion

This room covers the **foundational concepts** of computer networking:

- 🌍 **Networks** — connections between devices, from 2 to billions
- 🌐 **The Internet** — a massive public network of smaller private networks
- 🔢 **IP Addresses** — logical identifiers (IPv4 & IPv6), can be private or public
- 🔩 **MAC Addresses** — physical hardware identifiers, unique per device
- 📡 **Ping** — a basic tool using ICMP to test network connectivity

---

> 📚 **Next Room:** [Intro to LAN](https://tryhackme.com/room/introtolan) — Continue the Pre-Security path!

---

*Notes by **Sohel** | TryHackMe Pre-Security Learning Path*
