# 🔗 Chapter 6: The Link Layer and LANs (Detailed Notes)

---

## 🚦 6.1 Introduction to the Link Layer

- The **link layer** moves datagrams **between adjacent nodes** over a single link.
- Packets are **encapsulated** in link-layer **frames**.
- Key question: How are packets delivered over each link in an end-to-end path?

### ✈️ Analogy: Transportation
Like traveling with plane/train/bus hops, each link-layer handles one hop. Higher layers handle end-to-end.

---

## 🧠 6.2 Services Provided by the Link Layer

| Service | Description |
|--------|-------------|
| Framing | Encapsulate network-layer datagram |
| Link Access | Coordination over shared media (MAC) |
| Reliable Delivery | Retransmission, ACKs (rare in wired LANs) |
| Error Detection | Identify corrupted bits (e.g., CRC) |
| Error Correction | Identify + correct errors (e.g., Hamming) |
| Half-/Full-Duplex | Bidirectional data transmission options |

- **Error detection**: Parity, Checksum, CRC
- **Reliable delivery** mostly used in **wireless** links

---

## 💥 6.3 Multiple Access Links and Protocols

### Types of Links
1. **Point-to-point**: 1 sender, 1 receiver
2. **Broadcast**: Multiple devices share medium (e.g., Ethernet, WiFi)

### Multiple Access Protocol Categories:

| Type | Example | Idea |
|------|---------|------|
| **Channel Partitioning** | TDM, FDM | Divide time/frequency |
| **Random Access** | ALOHA, CSMA | Transmit when ready |
| **Taking Turns** | Polling, Token Ring | Controlled access |

### 🔀 Random Access Protocols

#### ALOHA
- Send and hope. Retransmit on collision.
- **Pure ALOHA**: Any time
- **Slotted ALOHA**: Time slots (better efficiency)

#### CSMA (Carrier Sense Multiple Access)
- Listen before transmit.
- CSMA/CD (with Collision Detection) for Ethernet.
- CSMA/CA (Collision Avoidance) for WiFi.

---

## 🔌 6.4 Switched LANs

### 6.4.1 Link-Layer Addressing

- **MAC Address**: 6-byte unique identifier for adapters.
- Used locally on a LAN.
- Not hierarchical like IP.

#### Address Resolution Protocol (ARP)
- Resolves IP → MAC.
- Maintains **ARP table** (cache).
- Works via **broadcasting** request and **unicast** reply.

---

### 6.4.2 Ethernet (IEEE 802.3)

- Dominant wired LAN technology.
- Uses CSMA/CD (for half-duplex) — mostly obsolete with full-duplex.
- **Frame format**:
  - Dest MAC | Src MAC | Type | Payload | CRC

- **Unreliable**, **connectionless**.

---

### 6.4.3 Link-Layer Switches

- Operate at **Layer 2**, no IP understanding.
- Use MAC tables to forward frames.
- **Self-learning**: learns which MACs are on which ports.
- Avoids collisions and supports simultaneous transmissions.

---

### 6.4.4 VLANs (Virtual LANs)

- Logical partitioning of physical LAN.
- VLAN tag added to Ethernet frames.
- Improves security and segmentation.

---

## 🏢 6.5 MPLS and Data Center Networks

### 🔁 MPLS (Multiprotocol Label Switching)
- Label-based forwarding (instead of IP lookup).
- Labels determine path (used by ISPs, data centers).

### 🏢 Data Center Networks
- Massive scale: hundreds of thousands of servers.
- Uses **Clos topology**, **load balancing**, and **traffic engineering**.

---

## ✅ 6.6 Summary of Link Layer

| Concept | Function |
|--------|----------|
| Framing | Encapsulate network-layer datagram |
| MAC Address | Local identification |
| Ethernet | Most common wired LAN protocol |
| ARP | IP-to-MAC translation |
| Switch | Layer 2 forwarding device |
| VLAN | Virtual network partitioning |
| MPLS | Fast forwarding using labels |

---

## 🧠 Interview Flashcards

1. **Why do we need MAC addresses if we already have IP addresses?**
   - MAC is local to the LAN; IP is global across networks.

2. **How does a switch know where to send a frame?**
   - It learns MAC-to-port mappings via self-learning.

3. **Difference between switch and router?**
   - Switch uses MAC addresses (Layer 2); router uses IP (Layer 3).

4. **What is ARP and how does it work?**
   - Maps IP → MAC. Sends broadcast query, receives unicast reply.

5. **What is CSMA/CD and where is it used?**
   - Ethernet collision detection, now mostly obsolete due to full-duplex links.

6. **What does VLAN do?**
   - Separates traffic logically on a single physical LAN.

---