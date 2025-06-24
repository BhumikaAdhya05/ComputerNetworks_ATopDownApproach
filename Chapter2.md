# 🌐 Chapter 2: Application Layer (Detailed Notes)

---

## 📌 2.1 Principles of Network Applications

### 👨‍💻 What Is a Network Application?
- Programs that **run on different end systems** and exchange messages.
- Communication does **not involve router programming**, only the end-hosts.

### 🧱 Application Architecture

#### 1. **Client-Server Model**
- **Server**: Always-on host with a fixed IP.
- **Client**: Initiates communication, does not communicate with other clients.
- Example: Web, FTP, Email.

#### 2. **Peer-to-Peer (P2P) Model**
- No always-on server.
- Peers communicate directly.
- Examples: BitTorrent, Skype (early), Napster.

---

### 🔄 2.1.2 Processes Communicating
- **Process**: Program running on a host.
- A sending process uses the transport layer to send messages to a receiving process.
- **Socket**: Interface between application and transport layer.

### 🔢 2.1.3 Addressing Processes
- Needs:
  - **IP address** of the host.
  - **Port number** (e.g., HTTP → 80, SMTP → 25).

### 💡 2.1.4 Transport Services

| Service | TCP | UDP |
|--------|-----|-----|
| Reliable Data Transfer | ✅ | ❌ |
| Flow Control | ✅ | ❌ |
| Congestion Control | ✅ | ❌ |
| Connection Setup | ✅ | ❌ |
| Timing, Throughput | ❌ | ✅ (better timing) |

### ⚙️ 2.1.5 Transport Service Requirements
- **Data loss tolerance** (e.g., video streaming).
- **Timing constraints** (e.g., VoIP).
- **Security** (e.g., HTTPS via SSL/TLS).

---

## 🌍 2.2 The Web and HTTP

### 📄 HyperText Transfer Protocol (HTTP)
- **Stateless**, **client-server**, **text-based** protocol.
- Uses TCP, default port: 80.

### 🔁 HTTP Protocol Versions
- **HTTP/1.0**: One request per connection.
- **HTTP/1.1**: Persistent connections (multiple requests on one TCP connection).

### 📤 HTTP Request Methods
- `GET`: Fetch resource.
- `POST`: Submit data (forms).
- `HEAD`: Header only.
- `PUT`: Upload resource.
- `DELETE`: Remove resource.

### 📥 HTTP Response Status Codes
- `200 OK`: Success
- `301 Moved Permanently`: Redirection
- `400 Bad Request`: Client error
- `404 Not Found`: Resource missing
- `505 HTTP Version Not Supported`

### 📦 Cookies
- Enable stateful sessions in HTTP.
- Components: `Cookie header`, `Set-Cookie`, backend storage.

### ⚡ Web Caching
- Store frequently accessed content close to clients.
- Uses: **Conditional GET**, `If-Modified-Since`.

---

## 📧 2.3 Email

### 📨 Email Components
- **User agents**: Outlook, Gmail app.
- **Mail servers**: Stores and forwards messages.
- **Protocols**: SMTP, POP3, IMAP.

### ✉️ SMTP (Simple Mail Transfer Protocol)
- Push-based.
- Uses TCP, port 25.
- Three phases:
  1. Handshake
  2. Transfer
  3. Closure

### 📥 Mail Access Protocols
| Protocol | Features |
|---------|----------|
| POP3 | Download and delete |
| IMAP | Remote folders, syncing |
| Webmail | HTTP-based |

---

## 🗂 2.4 DNS (Domain Name System)

### 🔍 Purpose
- Resolve human-readable names → IP addresses.

### 📚 DNS Hierarchy
- **Root servers**
- **TLD servers** (e.g., .com, .org)
- **Authoritative servers** (actual domain mapping)

### 🛠 Record Types
| Type | Description |
|------|-------------|
| A | Hostname → IPv4 |
| AAAA | Hostname → IPv6 |
| CNAME | Alias |
| NS | Name server |
| MX | Mail server |

### 📦 DNS Messages
- Format: query + response.
- Uses UDP, port 53.

### 💽 Caching
- Local DNS server caches responses.
- Includes TTL (Time To Live).

---

## 🤝 2.5 P2P Applications

### ⚡ Peer-to-Peer File Distribution
- Scalable model.
- Popular example: BitTorrent.

### 📥 BitTorrent
- File split into chunks.
- **Tracker** coordinates peers.
- Peers download/upload chunks to/from each other.

---

## 📹 2.6 Video Streaming and CDN

### 📼 Video Streaming
- Continuous delivery.
- Uses **buffering** to manage delay.

### 🔁 Adaptive Streaming (DASH)
- Dynamically selects video quality based on bandwidth.

### 🌐 Content Distribution Networks (CDNs)
- Replicate content across distributed servers.
- Reduces latency, offloads main servers.

---

## 💻 2.7 Socket Programming

### 🧠 Socket Basics
- Endpoint of a two-way communication.
- API: `socket()`, `bind()`, `listen()`, `accept()` (server), `connect()` (client).

### 💬 TCP Socket Programming
- Reliable, connection-oriented.
- Example: chat server, file transfer.

### 📡 UDP Socket Programming
- Unreliable, no connection setup.
- Example: simple DNS or streaming app.

---

## 🧾 2.8 Summary – Interview Key Takeaways

| Concept | Description |
|--------|-------------|
| Client-Server | Centralized server, multiple clients |
| P2P | Distributed, scalable, no always-on server |
| Socket | Interface for process-to-process comm |
| HTTP | Stateless, TCP-based web protocol |
| SMTP | Email sending protocol |
| DNS | Translates domain names to IP addresses |
| TCP vs UDP | Reliability vs speed tradeoff |
| CDN | Delivers content closer to the user |

---

## 🔑 Common Interview Q&A

1. **What transport protocol does HTTP use? Why?**
   - TCP, for reliable delivery and ordering.

2. **What makes HTTP stateless?**
   - Each request is independent; server does not retain info between requests.

3. **Why use Web caching?**
   - Reduces response time and server load.

4. **Difference between POP3 and IMAP?**
   - POP3 downloads & deletes; IMAP syncs across devices.

5. **What are cookies used for in HTTP?**
   - Track sessions and user state in a stateless protocol.

6. **Why is DNS hierarchical?**
   - Distributes load, increases scalability and fault-tolerance.

---