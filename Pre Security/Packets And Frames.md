# 📦 Packets & Frames — TryHackMe Notes

> **Author:** Sohel  
> **Room:** [Packets & Frames](https://tryhackme.com/room/packetsframes) — TryHackMe Pre-Security Learning Path  
> **Status:** ✅ Completed

---

## 📌 Table of Contents

- [Task 1 — What are Packets and Frames?](#task-1--what-are-packets-and-frames)
- [Task 2 — TCP/IP (The Three-Way Handshake)](#task-2--tcpip-the-three-way-handshake)
- [Task 3 — Practical: Handshake](#task-3--practical-handshake)
- [Task 4 — UDP/IP](#task-4--udpip)
- [Task 5 — Ports 101 (Practical)](#task-5--ports-101-practical)
- [Task 6 — Continue Your Learning](#task-6--continue-your-learning)
- [Conclusion](#conclusion)

---

## Task 1 — What are Packets and Frames?

When large data needs to be sent across a network, it is broken down into smaller units and transmitted individually, then reassembled at the destination.

### 📦 Packet

A **packet** is a unit of data transmitted across a network. It is a formatted block of information that contains:
- The **data** being transmitted
- **Control information** necessary for routing and delivery (IP addressing)

Packets are used in **network layer** protocols such as IP (Internet Protocol).

### 🖼️ Frame

A **frame** is a data transmission unit used at the **data link layer** of the OSI model. It:
- **Encapsulates** a packet from the network layer
- Adds information required for **link-layer delivery**
- Handles **physical addressing** and **error detection**
- Ensures the packet reaches the **next node** correctly

> A frame does **not** contain IP addressing information — it operates one layer below packets.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the name for a piece of data when it does have IP addressing information? | `Packet` |
| What is the name for a piece of data when it does not have IP addressing information? | `Frame` |

---

## Task 2 — TCP/IP (The Three-Way Handshake)

**TCP (Transmission Control Protocol)** is a connection-based protocol that guarantees reliable, ordered data delivery. Before data is sent, a connection is established through the **Three-Way Handshake**.

### TCP Packet Header Fields

| Field | Description | Purpose |
|-------|-------------|---------|
| **Source Port** | Port opened by the sender (randomly chosen from 0–65535) | Identifies the sending application |
| **Destination Port** | Port on the remote host (e.g. port 80 for web server) | Directs packet to the correct service |
| **Source IP** | IP address of the sending device | Identifies the origin of the packet |
| **Destination IP** | IP address of the receiving device | Ensures delivery to the correct recipient |
| **Sequence Number** | Randomly chosen number given to the first piece of data | Tracks order of data segments |
| **Acknowledgment Number** | Next expected sequence number (last received + 1) | Confirms which segments were received |
| **Checksum** | Calculated value used for error-checking | Validates data integrity during transit |
| **Data** | The actual payload being transmitted | Carries the content to the destination |
| **Flags** | Control bits (SYN, ACK, FIN, RST, PSH, URG) | Manages connection setup, transfer, and teardown |

### 🤝 The Three-Way Handshake

```
Client                          Server
  |                               |
  |-------- SYN ----------------->|   "Here's my ISN to synchronise with (0)"
  |                               |
  |<------- SYN/ACK --------------|   "Here's my ISN (5000), I ACK your ISN (0)"
  |                               |
  |-------- ACK ----------------->|   "I ACK your ISN (5000), here's ISN+1 (1)"
  |                               |
        Connection Established
```

| Step | Sender | Message | Meaning |
|------|--------|---------|---------|
| 1 | Client | `SYN` | Initiates connection, shares Initial Sequence Number |
| 2 | Server | `SYN/ACK` | Acknowledges client ISN, shares its own ISN |
| 3 | Client | `ACK` | Acknowledges server ISN — connection established |

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the header in a TCP packet that ensures the integrity of data? | `Checksum` |
| Provide the order of a normal Three-way handshake (each step separated by a comma) | `SYN,SYN/ACK,ACK` |

---

## Task 3 — Practical: Handshake

The practical involves carrying out a simulated TCP conversation following the correct handshake process. The connection goes through these stages in order:

| Flag | Sender | Description |
|------|--------|-------------|
| `SYN` | Client | Initial packet to initiate connection and synchronise devices |
| `SYN/ACK` | Server | Acknowledges the client's synchronisation attempt |
| `ACK` | Client/Server | Confirms that a series of messages have been received |
| `DATA` | Either | Actual data (e.g. bytes of a file) sent after connection is established |
| `FIN` | Either | Cleanly closes the connection once transfer is complete |

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the value of the flag given at the end of the conversation? | `THM{TCP_CHATTER}` |

---

## Task 4 — UDP/IP

**UDP (User Datagram Protocol)** is a **stateless** protocol — unlike TCP, it does not require a constant connection between devices and does not perform the Three-Way Handshake.

### UDP vs TCP

| Feature | TCP | UDP |
|---------|-----|-----|
| Connection type | Connection-based | Stateless |
| Reliable delivery | ✅ Yes | ❌ No |
| Ordered delivery | ✅ Yes | ❌ No |
| Speed | Slower | Faster |
| Use case | File transfer, Email | Video calls, Streaming |

> **UDP** trades reliability for speed — acceptable data loss makes it ideal for real-time applications where latency matters more than perfection.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What does the term "UDP" stand for? | `User Datagram Protocol` |
| What type of connection is "UDP"? | `Stateless` |
| What protocol would you use to transfer a file? | `TCP` |
| What protocol would you use to have a video call? | `UDP` |

---

## Task 5 — Ports 101 (Practical)

**Ports** are numerical identifiers (0–65535) that direct network traffic to the correct application or service on a device.

The practical involves connecting to a specific IP address and port to retrieve a flag:
- **IP Address:** `8.8.8.8`
- **Port:** `1234`

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the flag received from the challenge? | `THM{YOU_CONNECTED_TO_A_PORT}` |

---

## Task 6 — Continue Your Learning

> **Next Room:** Extending Your Network — diving deeper into how networks are expanded and connected.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| Terminate the static site lab deployed in tasks 3 and 5. | `No answer needed` |
| Join the "Extending Your Network" room to continue your learning. | `No answer needed` |

---

## Conclusion

This room covers how data is broken down and transmitted across a network:

- 📦 **Packets** — data units with IP addressing, used at the Network layer
- 🖼️ **Frames** — data units without IP addressing, used at the Data Link layer
- 🤝 **TCP Three-Way Handshake** — SYN → SYN/ACK → ACK establishes a reliable connection
- ✅ **TCP** — reliable, ordered, connection-based; best for file transfers and email
- ⚡ **UDP** — stateless, fast, no guaranteed delivery; best for video calls and streaming
- 🔌 **Ports** — numerical identifiers (0–65535) that route traffic to the correct service

---

*Notes by **Sohel** | TryHackMe Pre-Security Learning Path*
