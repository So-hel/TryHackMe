# 🖧 OSI Model — TryHackMe Notes

> **Author:** Sohel  
> **Room:** [OSI Model](https://tryhackme.com/room/osimodelzi) — TryHackMe Pre-Security Learning Path  
> **Status:** ✅ Completed

---

## 📌 Table of Contents

- [Task 1 — What is the OSI Model?](#task-1--what-is-the-osi-model)
- [Task 2 — Layer 7: Application](#task-2--layer-7-application)
- [Task 3 — Layer 6: Presentation](#task-3--layer-6-presentation)
- [Task 4 — Layer 5: Session](#task-4--layer-5-session)
- [Task 5 — Layer 4: Transport](#task-5--layer-4-transport)
- [Task 6 — Layer 3: Network](#task-6--layer-3-network)
- [Task 7 — Layer 2: Data Link](#task-7--layer-2-data-link)
- [Task 8 — Layer 1: Physical](#task-8--layer-1-physical)
- [Task 9 — Practical: OSI Game](#task-9--practical-osi-game)
- [Task 10 — Continue Your Learning](#task-10--continue-your-learning)
- [Conclusion](#conclusion)

---

## Task 1 — What is the OSI Model?

The **OSI (Open Systems Interconnection)** model is an absolute fundamental framework used in networking. It provides a standardized reference for how all networked devices **send**, **receive**, and **interpret** data.

The model is composed of **7 layers**, each responsible for a specific stage in data handling. As data travels through each layer, specific processes take place and pieces of information are added — this process is called **Encapsulation**.

### The 7 Layers at a Glance

| Layer | Name         | Primary Role                              |
|-------|--------------|-------------------------------------------|
| 7     | Application  | User-facing network services (GUI)        |
| 6     | Presentation | Data translation, encryption, compression |
| 5     | Session      | Connection establishment & management     |
| 4     | Transport    | Reliable data transfer via TCP / UDP      |
| 3     | Network      | Logical addressing & routing (IP)         |
| 2     | Data Link    | Physical addressing (MAC) & framing       |
| 1     | Physical     | Raw bit transmission over hardware        |

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What does the "OSI" in "OSI Model" stand for? | `Open Systems Interconnection` |
| How many layers (in digits) does the OSI model have? | `7` |
| What is the key term for when pieces of information get added to data? | `Encapsulation` |

---

## Task 2 — Layer 7: Application

The **topmost layer** of the OSI model — the layer that users interact with directly. It provides various network services to applications such as:

- Email
- File transfer
- Web browsing

Users interact with this layer through software exposed via a **Graphical User Interface (GUI)**.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the name of this Layer? | `Application` |
| What is the technical term given to the software that users interact with? | `Graphical User Interface` |

---

## Task 3 — Layer 6: Presentation

The **Presentation layer** acts as a **Translator** between the Application layer and the rest of the network. It formats or translates data based on the syntax or semantics that the application understands.

Additional responsibilities:
- **Data encryption** — secures data before transmission
- **Data compression** — reduces data size for efficient delivery

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the name of this Layer? | `Presentation` |
| What is the main purpose that this Layer acts as? | `Translator` |

---

## Task 4 — Layer 5: Session

The **Session layer** manages connections between applications. It is responsible for:

- **Establishing** connections (sessions) between devices
- **Maintaining** and synchronizing data exchanges throughout
- **Terminating** sessions once data transfer is complete

After synchronization, the Session layer divides outgoing data into smaller chunks called **Packets**, sending them one at a time.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the name of this Layer? | `Session` |
| What is the technical term for when a connection is successfully established? | `Session` |
| What is the technical term for "small chunks of data"? | `Packets` |

---

## Task 5 — Layer 4: Transport

The **Transport layer** ensures reliable data transfer between devices by:

- Controlling the flow of data
- Checking for and handling errors
- Ensuring data arrives in the correct order
- Breaking large messages into smaller **segments**

When data is sent between devices, it follows one of two protocols, chosen based on the needs of the application:

### 🔵 TCP — Transmission Control Protocol

- Reserves a **constant connection** between devices for the duration of the transfer
- Designed for **reliability and guaranteed delivery** of complete data
- **Synchronization** of both devices is required
- Best for: email clients, file downloads

### 🟡 UDP — User Datagram Protocol

- **Significantly faster** than TCP
- Does **not guarantee** delivery — does not care if data is received by the other device
- No synchronization required
- Best for: video streaming, real-time applications

### TCP vs UDP Comparison

| Feature           | TCP              | UDP              |
|-------------------|------------------|------------------|
| Reliable delivery | ✅ Yes           | ❌ No            |
| Speed             | Slower           | Faster           |
| Synchronization   | Required         | Not required     |
| Use case          | Email, Downloads | Video streaming  |

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the name of this Layer? | `Transport` |
| What does TCP stand for? | `Transmission Control Protocol` |
| What does UDP stand for? | `User Datagram Protocol` |
| What protocol guarantees the accuracy of data? | `TCP` |
| What protocol doesn't care if data is received or not by the other device? | `UDP` |
| What protocol would an application such as an email client use? | `TCP` |
| What protocol would an application that downloads files use? | `TCP` |
| What protocol would an application that streams video use? | `UDP` |

---

## Task 6 — Layer 3: Network

The **Network layer** determines the best path for data to travel from one network to another. It uses **logical (IP) addresses** to identify devices and route packets between networks.

Packets at this layer **will** take the most optimal route, determined by routing protocols such as:

| Protocol | Full Name                    | Role                             |
|----------|------------------------------|----------------------------------|
| OSPF     | Open Shortest Path First     | Determines optimal routing paths |
| RIP      | Routing Information Protocol | Distance-vector routing protocol |

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the name of this Layer? | `Network` |
| Will packets take the most optimal route across a network? (Y/N) | `Y` |
| What does the acronym "OSPF" stand for? | `Open Shortest Path First` |
| What does the acronym "RIP" stand for? | `Routing Information Protocol` |
| What type of addresses are dealt with at this layer? | `IP Addresses` |

---

## Task 7 — Layer 2: Data Link

The **Data Link layer** ensures reliable data transfer between adjacent network nodes. It:

- Packages data into **frames**
- Handles **error detection and correction** for accurate delivery
- Manages **physical (MAC) addressing** — adding the MAC address of the receiving endpoint to each packet

Every network-enabled device contains a **Network Interface Card (NIC)**, which comes pre-assigned with a unique **MAC (Media Access Control) address** used to identify it on the network.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the name of this Layer? | `Data Link` |
| What is the name of the piece of hardware that all networked devices come with? | `Network Interface Card` |

---

## Task 8 — Layer 1: Physical

The **lowest layer** of the OSI model. It handles the actual physical connection between devices and transmits raw data as electrical, optical, or radio signals.

Key hardware at this layer:
- **Ethernet cables** — used to connect devices
- **Switches and hubs**
- **Network Interface Cards (NICs)**

Data at this layer is represented in **binary** — a numbering system consisting entirely of `0`s and `1`s.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| What is the name of this Layer? | `Physical` |
| What is the name of the numbering system that is both 0's and 1's? | `Binary` |
| What is the name of the cables that are used to connect devices? | `Ethernet Cable` |

---

## Task 9 — Practical: OSI Game

An interactive dungeon game where you navigate a hacker through each OSI model layer in order (Layer 1 → Layer 7) using arrow keys. Successfully escaping the dungeon by reaching the seventh layer reveals the flag.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| Escape the dungeon to retrieve the flag. What is the flag? | `THM{OSI_DUNGEON_ESCAPED}` |

---

## Task 10 — Continue Your Learning

> **Next Room:** Packets & Frames — exploring how data is structured and transmitted across a network.

### ❓ Questions & Answers

| Question | Answer |
|----------|--------|
| Join the "Packets and Frames" room. | `No answer needed` |

---

## Conclusion

This room covers the 7 layers of the OSI model from top to bottom:

- 🖥️ **Application (L7)** — the user-facing layer; provides network services via GUIs
- 🔄 **Presentation (L6)** — translates, encrypts, and compresses data
- 🤝 **Session (L5)** — establishes, maintains, and terminates connections
- 🚚 **Transport (L4)** — ensures reliable delivery via TCP or fast delivery via UDP
- 🗺️ **Network (L3)** — routes packets between networks using IP addresses
- 🔗 **Data Link (L2)** — handles physical MAC addressing and frames data
- ⚡ **Physical (L1)** — transmits raw binary data over cables and hardware

---

*Notes by **Sohel** | TryHackMe Pre-Security Learning Path*
