# 🔁 Chapter 3: Transport Layer (Detailed Notes)

---

## 🚀 3.1 Introduction and Transport-Layer Services

- **Transport layer** provides **process-to-process** communication.
- Runs on **end systems only**, not on routers.
- Builds on top of **IP (network layer)**, which provides **host-to-host** communication.
- Main transport-layer protocols:
  - **TCP**: Reliable, connection-oriented.
  - **UDP**: Unreliable, connectionless.

### 🔄 Logical Communication
- From the app's point of view, it's as if it's directly connected to the remote process.
- Abstracts away routers, links, and protocols beneath it.

---

## 🧮 3.2 Multiplexing and Demultiplexing

- **Multiplexing**: Many apps use the same transport protocol (e.g., web, mail).
- **Demultiplexing**: Delivering data to the correct process (based on **port numbers**).

### 📥 Demultiplexing Steps
1. Extract destination IP and port number from segment.
2. Direct the segment to the appropriate socket.

### 🌐 Types
- **Connectionless (UDP)**:
  - Only uses destination port.
- **Connection-oriented (TCP)**:
  - Uses source & destination IP and ports.

---

## 📦 3.3 UDP – User Datagram Protocol

### 🔹 Features
- Simple, lightweight.
- No connection setup.
- Best-effort delivery (no reliability).
- Used in streaming, DNS, VoIP.

### 📄 Segment Structure
- Fields:
  - Source Port
  - Destination Port
  - Length
  - Checksum (for error checking)

### ✅ UDP Checksum
- Detects bit-level errors.
- Uses 1's complement addition.

---

## 🔁 3.4 Principles of Reliable Data Transfer (RDT)

### 🧪 Key Concepts
- Handles packet loss, corruption, duplication.

### ⚙️ RDT Versions
1. **rdt1.0** – No errors, stop-and-wait.
2. **rdt2.0** – Handles bit errors (with ACK/NAK).
3. **rdt2.1** – Adds sequence numbers.
4. **rdt3.0** – Adds timeout/retransmission (handles loss).

---

## 📍 3.4.2 Pipelined RDT Protocols

- **Stop-and-Wait**: Send one packet at a time (inefficient).
- **Pipelining**: Multiple packets sent without waiting.

### 🧱 Protocol Types

| Protocol | Description | Pros | Cons |
|---------|-------------|------|------|
| **Go-Back-N** | Sender sends N packets without ACK. Retransmits from error | Simple | Wasteful retransmissions |
| **Selective Repeat** | Only retransmit lost/erroneous packets | Efficient | Complex |

---

## 🌐 3.5 TCP – Transmission Control Protocol

### 🔗 3.5.1 TCP Connection
- **Three-way handshake**:
  1. SYN
  2. SYN-ACK
  3. ACK

### 📦 3.5.2 Segment Structure
- Source/Destination Ports
- Sequence & Acknowledgment Numbers
- Header Length
- Flags (SYN, FIN, ACK, RST, etc.)
- Receive Window
- Checksum
- Urgent Data Pointer (rarely used)

---

### ⏱ 3.5.3 Round-Trip Time Estimation (RTT)
- **EstimatedRTT** = (1 - α) × oldRTT + α × sampleRTT
- Timeout = EstimatedRTT + 4 × DevRTT

---

### 📡 3.5.4 TCP Reliable Data Transfer
- Uses:
  - Sequence numbers
  - ACKs
  - Cumulative ACK
  - Timeout and retransmission
  - **Fast Retransmit**: On 3 duplicate ACKs

---

### 🔄 3.5.5 Flow Control
- Prevents **receiver buffer overflow**.
- Receiver advertises available buffer via `rwnd`.

---

### 🔌 3.5.6 TCP Connection Management
- **Connection setup**: 3-way handshake
- **Connection teardown**: 4 segments (FIN, ACK pairs)

---

## ⚠️ 3.6 Principles of Congestion Control

### 📉 What is Congestion?
- Too much traffic → Queue overflow → Packet loss.

### 💰 Cost of Congestion
- Retransmissions waste bandwidth.
- Increases delay and packet drops.

---

## 📶 3.7 TCP Congestion Control

### 🧠 Mechanism
- Adjusts **sending rate** based on perceived congestion.

### 📊 Key Components
- **Congestion Window (cwnd)**: Limits unacknowledged data.
- **Slow Start**:
  - cwnd doubles every RTT until threshold.
- **Congestion Avoidance**:
  - Linear increase.
- **Fast Retransmit & Fast Recovery**:
  - On triple duplicate ACKs, retransmit + halve cwnd.

### 📈 Phases
1. Slow Start (cwnd = 1, double each RTT)
2. Congestion Avoidance (linear growth)
3. Fast Retransmit (skip timeout wait)
4. Fast Recovery

---

## 🧾 3.8 Summary – Interview Crib Sheet

| Feature | UDP | TCP |
|--------|-----|-----|
| Connection setup | ❌ | ✅ |
| Reliable delivery | ❌ | ✅ |
| Flow control | ❌ | ✅ |
| Congestion control | ❌ | ✅ |
| Ordering | ❌ | ✅ |
| Speed | Fast | Slower (overhead) |
| Use Cases | DNS, VoIP | HTTP, FTP, Email |

---

## 🧠 Interview Flashcards

1. **What is the transport layer's main job?**
   - Provide logical process-to-process communication.

2. **Why use UDP over TCP?**
   - Less overhead, lower latency, suitable for real-time use.

3. **What is the difference between Go-Back-N and Selective Repeat?**
   - GBN retransmits from error onward; SR retransmits only erroneous packets.

4. **What triggers TCP's Fast Retransmit?**
   - Three duplicate ACKs.

5. **How does TCP perform flow control?**
   - Receiver advertises available buffer size (`rwnd`).

6. **What is the purpose of TCP's congestion control?**
   - Prevent overwhelming the network and ensure fair bandwidth distribution.

---