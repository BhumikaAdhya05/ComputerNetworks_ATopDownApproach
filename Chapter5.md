# 🧠 Chapter 5: Network Layer – Control Plane (Detailed Notes)

---

## 🚦 5.1 Introduction

- The **Control Plane** is the **network-wide logic** for routing datagrams across routers.
- It determines:
  - **Forwarding tables** for each router (used by the Data Plane).
  - **Path selection** from source to destination.

### Two Approaches:

| Model | Description |
|-------|-------------|
| **Per-router control** | Each router runs a routing algorithm individually. |
| **Logically centralized control (SDN)** | A remote controller computes and installs routes across routers. |

---

## 📐 5.2 Routing Algorithms

Routing = Path computation in a **graph** (nodes = routers, edges = links with cost).

### 🔗 5.2.1 Link-State (LS) Routing Algorithm (e.g., OSPF)
- Each router knows **entire network topology** and link costs.
- Uses **Dijkstra’s Algorithm**.
- Steps:
  1. Initialize costs to neighbors.
  2. Iteratively add lowest-cost node.
  3. Update paths and costs.

### ➕ Pros
- Fast convergence
- Global knowledge → optimal paths

### ➖ Cons
- Scalability issues (high memory/computation)

---

### 📤 5.2.2 Distance-Vector (DV) Routing Algorithm (e.g., RIP)
- Routers only know costs to **neighbors**.
- Periodically exchange vectors with neighbors.
- Uses **Bellman-Ford Algorithm**.

### 📉 Problems
- **Count-to-Infinity**: Slow convergence on link failure.
- **Routing Loops**: Temporary incorrect paths.

### ➕ Pros
- Simple
- Low overhead

---

## 🏛 5.3 Intra-AS Routing (Interior Gateway Protocols – IGP)

- Runs **within an Autonomous System (AS)** (e.g., ISP, enterprise).
- **Open Shortest Path First (OSPF)** is most used.

### 🔍 OSPF Features:
- LS protocol
- Link states flooded to all routers.
- Uses **areas** for scalability.
- Supports **load balancing** and **authentication**.

---

## 🌍 5.4 Inter-AS Routing: BGP (Border Gateway Protocol)

- BGP = Routing **between ASes**
- Often called the "**glue of the Internet**"

### 🔗 Key Concepts:
- **eBGP**: between routers in different ASes.
- **iBGP**: within the same AS.

### 📡 BGP Advertisements
- Sent between neighbors
- Contain **prefixes** and **attributes**:
  - **AS-PATH**: List of ASes traversed
  - **NEXT-HOP**: IP address of next AS router

### 🎯 BGP Policy
- Policies decide:
  - Who to peer with
  - What routes to accept/advertise

---

## 🧠 5.5 The SDN Control Plane

- **Software-Defined Networking (SDN)** = Separation of control and data plane.

### 🧱 Architecture

1. **SDN Switches** (Data Plane)
   - Match+Action on flow tables

2. **SDN Controller** (Control Plane)
   - Maintains **network-wide state**
   - Installs flow rules in switches

3. **Network-Control Applications**
   - Routing
   - Access control
   - Load balancing

### 🔁 Interfaces

- **Southbound Interface** (e.g., OpenFlow):
  - Switch ↔ Controller communication

- **Northbound Interface**:
  - Controller ↔ Applications

---

## 🛰 5.6 ICMP – Internet Control Message Protocol

- Used for diagnostics and error reporting.

### 📑 ICMP Message Types:
- **Echo Request/Reply** (used in ping)
- **Destination Unreachable**
- **TTL Expired**

### 🎯 ICMP is not reliable or secure.

---

## 📊 5.7 Network Management and SNMP

### 🧱 5.7.1 Network Management Framework
- Components:
  - **Managed devices**
  - **Agents**: run on devices
  - **Network Management System (NMS)**: centralized controller

### 📋 5.7.2 SNMP – Simple Network Management Protocol
- Retrieves/sets device variables
- Uses **MIB (Management Information Base)**

---

## 🧾 5.8 Summary – Interview Flashcards

| Concept | Explanation |
|--------|-------------|
| Link-State (LS) | Each router has full map, runs Dijkstra |
| Distance-Vector (DV) | Routers share only neighbor distances |
| OSPF | Intra-AS LS protocol |
| BGP | Inter-AS DV protocol with policy control |
| SDN | Separates data/control plane |
| OpenFlow | Protocol between controller and switches |
| ICMP | Diagnostics (e.g., ping, traceroute) |
| SNMP | Network monitoring protocol |

---

## 🧠 Interview Q&A

1. **How does OSPF differ from BGP?**
   - OSPF is link-state within AS; BGP is policy-driven between ASes.

2. **Why is SDN considered programmable?**
   - Apps define behavior via APIs to a logically centralized controller.

3. **What is Count-to-Infinity in DV routing?**
   - A bad route slowly corrected via infinite updates.

4. **How does BGP prevent loops?**
   - By using the **AS-PATH** attribute.

5. **What does ICMP do?**
   - Reports errors and supports tools like `ping` and `traceroute`.

---