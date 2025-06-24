# 🎥 Chapter 9: Multimedia Networking (Detailed Notes)

---

## 🌐 9.1 Multimedia Networking Applications

### Types of Multimedia Applications:
1. **Streaming Stored Audio/Video**
   - Ex: Netflix, YouTube
   - Pre-recorded, delivered on-demand

2. **Conversational Voice/Video over IP (VoIP)**
   - Ex: Skype, Google Meet
   - Real-time interaction

3. **Streaming Live Audio/Video**
   - Ex: Twitch, live news streams
   - Real-time content distribution

---

## 📹 9.1.1 Properties of Video
- High bitrates: 100 kbps – 3 Mbps+
- Delay-sensitive but **loss-tolerant**
- Uses compression: MPEG, H.264

## 🎧 9.1.2 Properties of Audio
- Sampled analog signal (e.g., 8kHz, 8-bit = 64 kbps)
- Types:
  - Uncompressed: PCM
  - Compressed: MP3, AAC
- Also delay-sensitive and loss-tolerant

---

## ⏯ 9.2 Streaming Stored Video

### 🧰 Techniques:
- **Client Buffering**: Prevents underflow
- **Prefetching**: Reduces startup delay
- **Adaptive Streaming**: Adjusts quality to bandwidth

### 🚚 Streaming Types:
| Type | Description |
|------|-------------|
| **UDP Streaming** | Minimal delay, unreliable |
| **HTTP Streaming** | Reliable via TCP, uses HTTP |
| **DASH (Dynamic Adaptive Streaming over HTTP)** | Divides video into chunks with varying quality |

---

## ☎️ 9.3 Voice-over-IP (VoIP)

### 🚨 Challenges:
- Packet loss, jitter, delay
- Uses **best-effort IP** (no guarantees)

### 🧠 Techniques:
| Technique | Purpose |
|-----------|---------|
| Adaptive Playout | Adjusts delay to compensate jitter |
| Forward Error Correction (FEC) | Adds redundant data to recover lost packets |
| Error Concealment | Hides gaps (e.g., stretch or repeat audio) |

### 💬 Skype Case Study
- Uses **P2P overlay**, NAT traversal, encryption

---

## 📡 9.4 Protocols for Real-Time Conversational Apps

### 🟡 RTP – Real-Time Protocol
- Runs over UDP
- Includes:
  - Sequence numbers
  - Timestamps
  - Payload format

### 📞 SIP – Session Initiation Protocol
- Controls call setup, teardown
- Like HTTP + SMTP for VoIP
- Can negotiate codecs, IPs, and ports

---

## 🚦 9.5 Network Support for Multimedia

### 🧭 Key Concepts:
- **End-to-End Delay**: Total time for data delivery
- **Jitter**: Variability in delay
- **QoS (Quality of Service)**: Providing guaranteed performance

### 🧩 Tools for QoS:
| Tool | Function |
|------|----------|
| **Traffic Policing** | Drops excess packets |
| **Scheduling** | Fair queuing, priority queuing |
| **RSVP Protocol** | Resource reservation protocol |
| **DiffServ** | Differentiated services using DS field in IP header |

---

## 📋 9.6 Summary – Interview Cheat Sheet

| Concept | Summary |
|--------|---------|
| Multimedia Apps | Streaming, VoIP, Live |
| RTP | Real-time transport over UDP |
| SIP | Call/session control |
| DASH | Adaptive video via HTTP |
| QoS | Delay, jitter, loss guarantees |
| Buffering | Smooths playback |
| Jitter Compensation | Adaptive playout, FEC, concealment |

---

## 🧠 Interview Flashcards

1. **What are the three types of multimedia applications?**
   - Stored streaming, live streaming, conversational (VoIP)

2. **Why is UDP used in multimedia despite being unreliable?**
   - Provides low delay and loss-tolerance is acceptable

3. **What’s the role of RTP in multimedia?**
   - Provides timing and sequencing for media streams over UDP

4. **How does DASH improve user experience?**
   - Adapts video quality to current bandwidth conditions

5. **What is jitter, and how can it be mitigated?**
   - Variation in delay; mitigated by buffers and adaptive playout

6. **Compare SIP and RTP.**
   - SIP handles session setup; RTP carries media content

7. **What is traffic policing?**
   - Limits traffic flow and drops excess packets

---