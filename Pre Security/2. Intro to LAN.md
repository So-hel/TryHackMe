# 🖧 Intro to LAN — TryHackMe Notes

> **Author:** Sohel  
> **Room:** [Intro to LAN](https://tryhackme.com/room/introtolan) — TryHackMe Pre-Security Learning Path  
> **Status:** ✅ Completed

---

## 📌 Table of Contents

- [LAN Topologies](#lan-topologies)
- [Switches & Routers](#switches--routers)
- [Subnetting](#subnetting)
- [ARP Protocol](#arp-protocol)
- [DHCP Protocol](#dhcp-protocol)
- [Task Answers](#task-answers)
- [Conclusion](#conclusion)

---

## LAN Topologies

**LAN** stands for **Local Area Network**. A **topology** refers to the design or layout of a network. There are 3 main topologies:

---

### ⭐ Star Topology

Devices are individually connected to a **central networking device** (switch or hub).

| Pros | Cons |
|------|------|
| Most reliable & scalable | More expensive (extra cabling + hardware) |
| Easy to add new devices | More maintenance as network grows |
| Widely used today | If central device fails, all devices disconnect |

---

### 🚌 Bus Topology

All devices connect along a **single backbone cable**, like leaves on a branch.

| Pros | Cons |
|------|------|
| Easy and cost-efficient to set up | Prone to bottlenecks |
| Less cabling required | Hard to troubleshoot |
| | No redundancy — if cable breaks, everything fails |

---

### 🔁 Ring Topology

Devices are connected **directly to each other** in a loop. Data travels around the loop until it reaches its destination.

| Pros | Cons |
|------|------|
| Easy to troubleshoot | Not efficient — data may pass through many devices |
| Less cabling needed | A single fault (cut cable/broken device) breaks the entire network |
| Less prone to bottlenecks | |

---

## Switches & Routers

### 🔀 Switches

- Dedicated devices that **connect multiple devices** on a local network using ethernet
- Available with 4, 8, 16, 24, 32, or 64 ports
- **Smarter than hubs** — they track which device is on which port and send packets only to the intended target (reducing unnecessary traffic)
- Switches and Routers can be connected together to add **redundancy** — if one path goes down, another can be used

### 🔁 Routers

- A router's job is to **connect networks** and pass data between them
- Uses **routing** — the process of creating a path between networks for data to travel
- Useful when devices are connected by many paths

---

## Subnetting

**Subnetting** is the process of splitting a network into smaller pieces, managed using a **subnet mask**.

- An IP address and subnet mask are both made up of **4 octets (32 bits)**, ranging from **0–255**

Subnets use IP addresses in **3 ways**:

| Type | Description | Example |
|------|-------------|---------|
| **Network Address** | Identifies the start/existence of the network | `192.168.1.0` |
| **Host Address** | Identifies a specific device on the subnet | `192.168.1.100` |
| **Default Gateway** | Device responsible for sending data to another network | `192.168.1.1` or `192.168.1.254` |

### Why is Subnetting useful?

- ✅ **Efficiency** — organises and categorises the network
- ✅ **Security** — separates different use cases
- ✅ **Control** — full management of who can access what

> **Example:** A café might have two separate subnets — one for staff/cash registers and one for public Wi-Fi hotspot.

---

## ARP Protocol

**ARP (Address Resolution Protocol)** allows devices to associate their **MAC address with an IP address** on a network.

### How ARP works:

```
Device A wants to talk to Device B
        |
        ↓
Device A sends ARP Request (broadcast to entire network)
"Who has IP 192.168.1.5? Tell me your MAC address."
        |
        ↓
Device B responds with ARP Reply
"That's me! My MAC address is a4:c3:f0:85:ac:2d"
        |
        ↓
Device A stores this in its ARP Cache
```

| Message | Purpose |
|---------|---------|
| **ARP Request** | Broadcast asking which device has a specific IP |
| **ARP Reply** | Response confirming the MAC address |

- **MAC Address** → Physical identifier
- **IP Address** → Logical identifier
- **ARP Cache** → Local ledger where devices store MAC-to-IP mappings

---

## DHCP Protocol

**DHCP (Dynamic Host Configuration Protocol)** automatically assigns IP addresses to devices on a network.

### DHCP Process (4 steps):

```
1. DHCP Discover  → Device broadcasts: "Is there a DHCP server?"
2. DHCP Offer     → Server replies: "You can use this IP address."
3. DHCP Request   → Device confirms: "Yes, I'll take that IP."
4. DHCP ACK       → Server acknowledges: "Done! IP is yours."
```

> IP addresses can also be assigned **manually** (static), but DHCP is the most common method.

---

## Task Answers

### ✅ Task 1 — LAN Topologies

| Question | Answer |
|----------|--------|
| What does LAN stand for? | `Local Area Network` |
| What is the verb given to the job that Routers perform? | `Routing` |
| What device centrally connects multiple devices and transmits data to the correct location? | `Switch` |
| What topology is cost-efficient to set up? | `Bus Topology` |
| What topology is expensive to set up and maintain? | `Star Topology` |
| Flag from the interactive lab? | `THM{TOPOLOGY_FLAWS}` |

---

### ✅ Task 2 — Subnetting

| Question | Answer |
|----------|--------|
| What is the technical term for dividing a network into smaller pieces? | `Subnetting` |
| How many bits are in a subnet mask? | `32` |
| What is the range of a section (octet) of a subnet mask? | `0-255` |
| What address identifies the start of a network? | `Network Address` |
| What address identifies devices within a network? | `Host Address` |
| What is the device responsible for sending data to another network called? | `Default Gateway` |

---

### ✅ Task 3 — ARP Protocol

| Question | Answer |
|----------|--------|
| What does ARP stand for? | `Address Resolution Protocol` |
| What category of ARP packet asks a device whether it has a specific IP address? | `Request` |
| What address is used as a physical identifier for a device? | `MAC Address` |
| What address is used as a logical identifier for a device? | `IP Address` |

---

### ✅ Task 4 — DHCP Protocol

| Question | Answer |
|----------|--------|
| What type of DHCP packet does a device use to retrieve an IP address? | `DHCP Discover` |
| What type of DHCP packet does a device send once offered an IP address? | `DHCP Request` |
| What is the last DHCP packet sent from a server to a device? | `DHCP ACK` |

---

## Conclusion

This room covers the core concepts of Local Area Networks:

- 🖧 **LAN Topologies** — Star (reliable but costly), Bus (cheap but bottlenecks), Ring (loop-based but a single fault breaks everything)
- 🔀 **Switches** — smarter than hubs, send data only to the intended device
- 🔁 **Routers** — connect different networks together using routing
- 📐 **Subnetting** — splits a network into smaller parts for efficiency, security and control
- 📡 **ARP Protocol** — maps IP addresses to MAC addresses using Request & Reply messages
- 🌐 **DHCP Protocol** — automatically assigns IP addresses through a 4-step process (Discover → Offer → Request → ACK)


---

*Notes by **Sohel** | TryHackMe Pre-Security Learning Path*
