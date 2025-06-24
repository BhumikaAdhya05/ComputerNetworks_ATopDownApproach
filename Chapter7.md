# 📶 Chapter 7: Wireless and Mobile Networks (Detailed Notes)

---

## 🌐 7.1 Introduction

- **Wireless ≠ Mobility**:
  - **Wireless**: No physical cables (e.g., WiFi laptop).
  - **Mobility**: Changing point of attachment over time (e.g., mobile device on the move).

### 🔍 Network Context
- Wireless devices access the **wired network infrastructure** via **wireless links** and **base stations**.
- Challenges arise from:
  - Unreliable wireless transmission
  - User movement (mobility)

---

## 📡 7.2 Wireless Links and Network Characteristics

### 📊 Characteristics of Wireless Links
| Impairment | Description |
|------------|-------------|
| Path loss | Signal weakens with distance |
| Interference | Other transmissions collide |
| Multipath fading | Reflections cause interference |
| Variable rate | Due to dynamic channel conditions |

### 🛠 CDMA (Code Division Multiple Access)
- **Each user has a unique code**.
- Signals from different users are **spread over frequency spectrum** and **separated by correlating codes**.
- Used in 3G networks.

---

## 📶 7.3 WiFi – IEEE 802.11 Wireless LANs

### 🖧 Components
- **Stations (STAs)**: Clients (laptops, phones)
- **Access Points (APs)**: Base stations
- **BSS**: Basic Service Set (one AP + STAs)
- **ESS**: Extended Service Set (multiple APs)

### 🔄 Medium Access in 802.11
- Uses **CSMA/CA** (Collision Avoidance) instead of CD
- **ACK-based reliability**

### 🧩 Protocol Phases
- **Scanning**: Passive or Active
- **Association**: STA connects to AP
- **Authentication**: Security exchange

### 📋 Frame Structure
- Frame Control, Duration, Addr1–Addr3, Seq Control, Data, CRC

### 📶 RTS/CTS Mechanism
- Optional collision avoidance using short control frames.

---

## 📲 7.4 Cellular Internet Access

### 📶 Generations
| Generation | Features |
|------------|----------|
| 1G | Analog voice |
| 2G | Digital voice (e.g., GSM) |
| 3G | Voice + data (packet switching) |
| 4G | All IP (LTE, OFDM) |
| 5G | Ultra-low latency, mmWave, massive IoT |

### 🧱 3G Architecture
- Core + Radio Access Network
- Key Components:
  - RNC (Radio Network Controller)
  - SGSN (Serving GPRS Support Node)
  - GGSN (Gateway GPRS Support Node)

### 🚀 4G/LTE Components
- **eNodeB**: Enhanced Node B (radio base station)
- **MME**: Mobility Management Entity
- **SGW/PGW**: Gateways for tunneling IP traffic

---

## 🚗 7.5 Mobility Management – Principles

### 🧳 Types of Mobility
- **No mobility**: Stationary device
- **Device mobility**: Moves but not while communicating
- **Session mobility**: Communication continues across movement

### 🎯 Key Functions
- **Handoff**: Switching access points during movement
- **Location management**: Where is the user?
- **Routing to mobile users**

---

## 🌍 7.6 Mobile IP

### 📍 Goals
- Maintain IP address during movement.
- Transparent to transport/application layers.

### 👥 Roles
| Role | Function |
|------|----------|
| Home Agent (HA) | Acts on behalf of the mobile |
| Foreign Agent (FA) | Provides care-of address |
| Mobile Node (MN) | The device |

- Uses **triangular routing** via HA → FA → MN.

---

## 📞 7.7 Mobility in Cellular Networks (GSM & LTE)

### GSM Mobility
- Involves **Mobile Switching Center (MSC)** and **Visitor Location Register (VLR)**.
- Location updates during movement.

### LTE Mobility
- Supports **seamless handoff** using tunneling and soft transitions.

---

## 🧬 7.8 Impact on Higher-Layer Protocols

### 🪫 Challenges for TCP
- Assumes packet loss = congestion
- Mobility/wireless can also cause loss
- **Split TCP** and **Link-layer retransmission** help

### 🌐 Application Layer Impact
- Apps must consider **low bandwidth**, **latency**, and **variable quality**.

---

## 🧾 7.9 Summary – Interview Crib Sheet

| Topic | Key Points |
|-------|------------|
| WiFi | Uses CSMA/CA, ACK, AP-based BSS |
| Cellular | Evolves from voice (2G) to IP (4G/5G) |
| CDMA | Multiple users on shared medium via codes |
| Mobility | Handoff, location, routing |
| Mobile IP | Keeps IP fixed with home/foreign agent |
| LTE | All-IP, high speed, seamless handoff |
| TCP in Wireless | Retransmission and splitting improve performance |

---

## 🧠 Interview Flashcards

1. **Why does WiFi use CSMA/CA instead of CSMA/CD?**
   - Collisions can't be detected reliably in wireless.

2. **How is mobility managed in GSM?**
   - Via location areas, VLR, MSC, and handoff procedures.

3. **What is the role of the MME in LTE?**
   - Manages mobility and session setup.

4. **Why is TCP inefficient in wireless?**
   - Mistakes packet loss from link issues as congestion.

5. **What does Mobile IP solve?**
   - Allows a host to maintain the same IP while moving across networks.

---