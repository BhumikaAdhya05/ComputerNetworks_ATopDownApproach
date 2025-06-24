# 🔐 Chapter 8: Security in Computer Networks (Detailed Notes)

---

## 🧭 8.1 What Is Network Security?

**Security Goals for Alice ↔ Bob:**
1. **Confidentiality** – prevent eavesdropping
2. **Authentication** – verify identity
3. **Integrity** – detect tampering
4. **Availability** – prevent DoS attacks

### Common Threats
- Eavesdropping
- Tampering (modification, deletion)
- Masquerading
- Replay attacks
- Denial of Service (DoS)
- Malware (viruses, worms, trojans)

---

## 🔐 8.2 Principles of Cryptography

### 8.2.1 Symmetric Key Cryptography
- Same key used for encryption and decryption.
- Examples: AES, DES
- **Key challenge**: secure key distribution.

### 8.2.2 Public Key Cryptography
- **Asymmetric**: Public key for encryption, private for decryption.
- Examples: RSA, ElGamal
- Enables **secure key exchange** and **digital signatures**.

---

## 🛡 8.3 Message Integrity and Digital Signatures

### 8.3.1 Cryptographic Hash Functions
- Fixed-length output
- Properties:
  - Collision-resistant
  - One-way (irreversible)
- Example: SHA-256

### 8.3.2 Message Authentication Code (MAC)
- Used with symmetric keys: `MAC = F(K, m)`
- Ensures integrity + source authentication.

### 8.3.3 Digital Signatures
- Uses sender’s **private key**.
- Provides **non-repudiation**, integrity, and sender authentication.

---

## 🔑 8.4 End-Point Authentication

### Protocol Techniques:
- **Challenge-response** using nonces
- Authentication Protocols:
  - ap1.0: simple password
  - ap2.0: replay attack vulnerability
  - ap3.0: nonce + shared key
  - ap4.0: nonce + public key

---

## 📧 8.5 Securing E-Mail

### Goals:
- Confidentiality
- Integrity
- Authentication

### Techniques:
- **PGP (Pretty Good Privacy)**:
  - Uses both symmetric and public key encryption
  - Digitally signs messages

---

## 🔒 8.6 Securing TCP Connections – SSL

### 8.6.1 SSL Overview
- Provides:
  - Confidentiality (encryption)
  - Authentication (certificates)
  - Integrity (MACs)

- Works **above TCP**, used by HTTPS.

### 8.6.2 SSL Handshake
1. ClientHello (includes random number)
2. ServerHello + certificate
3. Client verifies cert
4. Client generates secret
5. Secure session begins

---

## 🌐 8.7 IPsec – Network Layer Security

### 8.7.1 VPNs with IPsec
- Encrypts IP datagrams for **blanket coverage**
- Uses **Security Associations (SAs)**

### 8.7.2 AH vs ESP
- AH: Authentication Header (integrity only)
- ESP: Encapsulating Security Payload (integrity + confidentiality)

### 8.7.5 IKE (Internet Key Exchange)
- Used for key management and SA negotiation.

---

## 📶 8.8 Securing Wireless LANs

### 8.8.1 WEP (Wired Equivalent Privacy)
- Uses RC4 + shared key
- Vulnerable to attacks due to weak IV (Initialization Vector)

### 8.8.2 802.11i (WPA/WPA2)
- Uses:
  - **EAP** (Extensible Authentication Protocol)
  - **AES-based encryption (CCMP)**
  - **Robust security association protocols**

---

## 🧱 8.9 Operational Security

### 8.9.1 Firewalls
- **Stateless**: Filters based on IP/TCP headers
- **Stateful**: Tracks connection state
- **Application Layer**: Understands protocols (e.g., HTTP)

### 8.9.2 Intrusion Detection Systems (IDS)
- Monitors traffic for known attack patterns
- Can be host-based or network-based

---

## 🧾 8.10 Summary – Key Concepts

| Concept | Function |
|--------|----------|
| Cryptography | Secure communication |
| MAC | Message integrity with symmetric keys |
| Digital Signature | Message integrity + non-repudiation |
| SSL | Transport layer security |
| IPsec | Network layer security |
| WEP/WPA | WiFi security |
| Firewalls | Prevent unauthorized access |
| IDS | Detect attacks |

---

## 🧠 Interview Flashcards

1. **What are the goals of network security?**
   - Confidentiality, Integrity, Authentication, Availability

2. **Difference between MAC and Digital Signature?**
   - MAC: symmetric, no non-repudiation
   - Signature: asymmetric, provides non-repudiation

3. **Why is public key cryptography useful?**
   - Secure key exchange, digital signatures

4. **How does SSL differ from IPsec?**
   - SSL: Transport layer (application-specific)
   - IPsec: Network layer (blanket encryption)

5. **Why is WEP insecure?**
   - Weak IV reuse leads to key recovery

6. **How do firewalls protect a network?**
   - Filter traffic based on rules (IP, port, state)

---