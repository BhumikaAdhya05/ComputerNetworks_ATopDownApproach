# 🌐 Chapter 4: The Network Layer – Data Plane (Detailed Notes)

---

## 🧭 4.1 Overview of the Network Layer

- The **network layer** moves packets (datagrams) from one host to another via intermediate routers.
- It provides a **host-to-host** communication service for the **transport layer**.
- **Two Main Functions**:
  - **Forwarding (Data Plane)**: Per-router task of moving a packet from input link to correct output link.
  - **Routing (Control Plane)**: Network-wide process to determine the path taken by packets.

### 🛣 Forwarding vs Routing
| Function | Description | Scope |
|----------|-------------|-------|
| Forwarding | Local process at each router to move packets | Per-router |
| Routing | Global process to compute paths | Across network |

---

## 📦 4.2 What’s Inside a Router?

A router has 4 main components:

### 4.2.1 Input Port
- Functions:
  - Receive packet
  - Perform lookup to determine output port (based on destination IP)
  - Use **forwarding table**

### 4.2.2 Switching Fabric
- Transfers packets from input to output ports.
- Architectures:
  - **Memory-based**: Simple but slow.
  - **Bus-based**: One packet at a time.
  - **Interconnection networks**: High-speed, modern.

### 4.2.3 Output Port
- Buffers packets before transmission.
- Schedules packet transmission.

### 4.2.4 Where Does Queuing Occur?
- **Input queuing**: If switching fabric is slow.
- **Output queuing**: If outbound link is slow.

### 4.2.5 Packet Scheduling
- Determines the order of packet transmission.
- Algorithms:
  - **FIFO**
  - **Priority queueing**
  - **Round Robin**
  - **Weighted Fair Queueing (WFQ)**

---

## 🌐 4.3 Internet Protocol (IP)

### 4.3.1 IPv4 Datagram Format
| Field | Description |
|-------|-------------|
| Version | IPv4 or IPv6 |
| Header Length | In 32-bit words |
| Type of Service | QoS support |
| Total Length | Header + data |
| Identification, Flags, Fragment Offset | Fragmentation |
| TTL | Prevent infinite loops |
| Protocol | Next layer (e.g., TCP=6, UDP=17) |
| Header Checksum | Error check |
| Source & Destination Address | Routing info |

### 4.3.2 Fragmentation
- Divides large datagrams for transport.
- Each fragment has:
  - ID
  - Offset
  - More fragments flag

### 4.3.3 IPv4 Addressing
- 32-bit addresses (e.g., 192.168.1.1)
- **CIDR** format: a.b.c.d/x
- **Subnetting**: Split large networks
- **DHCP**: Dynamic address assignment
- **NAT**: Maps multiple internal IPs to a single public IP

### 4.3.4 Network Address Translation (NAT)
- Hides internal IPs
- Conserves IPv4 addresses
- **NAT table**: Maps (internal IP, port) ↔ (external IP, port)

### 4.3.5 IPv6
- 128-bit addresses
- Simplified header:
  - No fragmentation
  - No checksum
- **Transition mechanisms**:
  - Dual stack
  - Tunneling

---

## 🧠 4.4 Generalized Forwarding and SDN

### 🔍 4.4.1 Match
- Packets are matched on fields:
  - IP address, port, protocol type, etc.

### 🛠 4.4.2 Action
- Forward
- Drop
- Modify header
- Duplicate

### 🔄 4.4.3 SDN with OpenFlow
- Uses **flow tables**:
  - Match + Action
- **Centralized controller** computes flow tables.
- Examples:
  - Firewalls
  - Load balancers
  - Virtual networks

---

## 🧾 4.5 Summary – Interview Ready Takeaways

### 🎯 Key Concepts

| Concept | Description |
|--------|-------------|
| Forwarding | Router action: input → output |
| Routing | Path computation from source to destination |
| IP Datagram | Basic unit of data at network layer |
| Fragmentation | Splitting datagrams to fit MTU |
| NAT | One public IP ↔ multiple private IPs |
| IPv6 | Successor to IPv4, 128-bit addressing |
| SDN | Centralized control of forwarding behavior |

---

## 💡 Interview Flashcards

1. **What is the difference between forwarding and routing?**
   - Forwarding is local; routing is global.

2. **What are the main fields in the IPv4 header?**
   - Version, Total Length, TTL, Protocol, Source/Dest IP.

3. **Why was NAT introduced?**
   - To reduce IPv4 address exhaustion.

4. **What does a router do internally?**
   - Input port → Lookup → Switch fabric → Output port.

5. **How is IPv6 better than IPv4?**
   - Larger address space, no NAT, simplified header.

6. **What is the role of the SDN controller?**
   - Computes and installs flow rules in switches.

---