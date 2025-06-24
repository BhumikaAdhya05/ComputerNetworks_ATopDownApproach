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
4