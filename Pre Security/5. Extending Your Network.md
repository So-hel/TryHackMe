# 🌐 Extending Your Network — TryHackMe Notes

> **Author:** Sohel  
> **Room:** [Extending Your Network](https://tryhackme.com/room/extendingyournetwork) — TryHackMe Pre-Security Learning Path  
> **Status:** ✅ Completed

---

## 📌 Table of Contents

- [Task 1 — Introduction to Port Forwarding](#task-1--introduction-to-port-forwarding)
- [Task 2 — Firewall](#task-2--firewall)
- [Task 3 — VPN Basics](#task-3--vpn-basics)
- [Task 4 — LAN Networking Devices](#task-4--lan-networking-devices)
- [Task 5 — Practical: Network Simulator](#task-5--practical-network-simulator)
- [Conclusion](#conclusion)

---

## Task 1 — Introduction to Port Forwarding

**Port Forwarding** is an essential component in connecting applications and services to the Internet. Without it, applications and services such as web servers are only available to devices within the same direct network.

If an administrator wants a website to be accessible to the public over the Internet, they must implement port forwarding — configured on the **Router** — to forward incoming traffic on a specific port to the correct internal device.

> **Example:** A web server running internally on port 80 can be made publicly accessible by configuring the router to forward external requests on port 80 to the server's private IP address.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the name of the device that is used to configure port forwarding? | `Router` |

---

## Task 2 — Firewall

A **Firewall** is a device within a network responsible for determining what traffic is allowed to enter and exit. It can be configured to **permit** or **deny** traffic based on factors such as:

- Protocol
- Port number
- Source/destination IP address

Firewalls operate at **Layer 3 (Network)** and **Layer 4 (Transport)** of the OSI model.

### 🔥 Firewall Types

| Type | How it works |
|------|-------------|
| **Stateful** | Inspects the **entire connection** — makes decisions based on the full context of a session |
| **Stateless** | Inspects **individual packets** — works strictly within predefined rules, with no awareness of connection state |

### 🛡️ Practical — Firewall Room

The practical requires correctly configuring a firewall to prevent a device from overloading in order to retrieve the flag.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What layers of the OSI model do firewalls operate at? | `Layer 3, Layer 4` |
| What category of firewall inspects the entire connection? | `Stateful` |
| What category of firewall inspects individual packets? | `Stateless` |

---

## Task 3 — VPN Basics

A **VPN (Virtual Private Network)** is a technology that allows devices on separate networks to communicate securely by creating a dedicated encrypted path between each other over the Internet — known as a **tunnel**.

### ✅ Benefits of a VPN

- **Privacy** — hides your traffic from third parties
- **Anonymity** — masks your real IP address
- **Security** — encrypts data in transit

### 🔐 VPN Technologies

| Technology | Full Name | Description |
|------------|-----------|-------------|
| **PPP** | Point-to-Point Protocol | Encrypts data and provides authentication — but does not provide tunnelling on its own |
| **PPTP** | Point-to-Point Tunnelling Protocol | Very easy to set up but weakly encrypted compared to alternatives |
| **IPSec** | Internet Protocol Security | Encrypts data using the existing IP framework; offers strong encryption |

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What VPN technology only encrypts & provides the authentication of data? | `PPP` |
| What VPN technology uses the IP framework? | `IPSec` |

---

## Task 4 — LAN Networking Devices

### 🔁 Router

- Connects networks and passes data between them using **routing**
- Operates at **Layer 3** (Network layer) of the OSI model

### 🔀 Switch

- A dedicated networking device that connects multiple devices together
- Can facilitate many devices (3–63) using Ethernet cables
- Can operate at **Layer 2** (Data Link) or **Layer 3** (Network) of the OSI model

### Layer Comparison

| Device | OSI Layer | Primary Role |
|--------|-----------|--------------|
| Router | Layer 3 | Connects and routes between networks |
| Switch | Layer 2 / Layer 3 | Connects multiple devices within a network |

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the verb for the action that a router does? | `Routing` |
| What are the two different layers of switches? (LayerX,LayerY) | `Layer2,Layer3` |

---

## Task 5 — Practical: Network Simulator

The practical involves using a network simulator to send a **TCP packet** from `computer1` to `computer3`. The packet travels through the network following the TCP Three-Way Handshake process before delivering the data and revealing the flag.

### TCP Packet Flow in Simulator

```
computer1  →  [SYN]        →  computer3
computer1  ←  [SYN/ACK]    ←  computer3
computer1  →  [ACK]        →  computer3
computer1  →  [DATA]       →  computer3
            (Flag revealed)
```

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the flag from the network simulator? | `THM{YOU'VE_GOT_DATA}` |
| How many HANDSHAKE entries are there in the Network Log? | `5` |

---

## Conclusion

This room covers the key components used to extend and secure a network:

- 🔌 **Port Forwarding** — configured on a Router to make internal services accessible over the Internet
- 🔥 **Firewall** — controls inbound/outbound traffic at Layer 3 & 4; Stateful inspects full connections, Stateless inspects individual packets
- 🔐 **VPN** — creates encrypted tunnels between networks; PPP authenticates, PPTP is easy but weak, IPSec is strong and IP-based
- 🔁 **Router** — routes data between networks at Layer 3
- 🔀 **Switch** — connects multiple devices within a network at Layer 2 or Layer 3

---

*Notes by **Sohel** | TryHackMe Pre-Security Learning Path*
