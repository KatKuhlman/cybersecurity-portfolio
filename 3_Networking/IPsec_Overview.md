# IPsec Overview

This document provides a structured explanation of IPsec (Internet Protocol Security), including its purpose, components, operating modes, authentication mechanisms, and key exchange process. It also includes ASCII diagrams to visualize packet encapsulation and tunnel behavior. The goal is to give a clear, practical understanding of how IPsec protects network traffic.

---

## Purpose of IPsec

IPsec is a suite of protocols designed to secure IP traffic by providing:

- **Confidentiality** (encryption)
- **Integrity** (ensuring data is unchanged)
- **Authentication** (verifying peers)
- **Anti-replay protection** (preventing packet reuse attacks)

IPsec operates at the **Network Layer (Layer 3)**, allowing it to protect any IP-based protocol without modifying applications.

---

## Core IPsec Components

IPsec consists of two primary security protocols:

### **Authentication Header (AH)**  
- Provides integrity and authentication  
- Does **not** provide encryption  
- Protects most of the IP header  
- Rarely used today due to compatibility issues with NAT

### **Encapsulating Security Payload (ESP)**  
- Provides encryption, integrity, and authentication  
- More widely used  
- NAT-friendly  
- Supports confidentiality by encrypting payloads

---

## IPsec Operating Modes

IPsec can operate in one of two modes depending on the traffic and environment.

### **Transport Mode**
- Protects **only the payload** of the IP packet  
- Original IP header remains intact  
- Common for host-to-host communication  
- Lower overhead  

#### ASCII representation:

```
[ Original IP Header ][ ESP Header ][ Encrypted Payload ][ ESP Trailer ][ Auth Data ]
```

---

### **Tunnel Mode**
- Protects the **entire original IP packet**  
- Wraps it inside a new IP header  
- Common for VPN gateways or site-to-site VPNs  
- Provides full encapsulation  

#### ASCII representation:

```
[ New IP Header ][ ESP Header ][ Original IP Header + Payload Encrypted ][ ESP Trailer ][ Auth ]
```

Tunnel mode is the default for site-to-site VPN configurations.

---

## Security Associations (SAs)

A **Security Association** defines the parameters of an IPsec session.  
An SA includes:

- Encryption algorithm  
- Integrity algorithm  
- Keys  
- Lifetime  
- Mode (tunnel/transport)  
- SPI (Security Parameter Index)

Two SAs are required:  
- One for traffic **outbound**  
- One for traffic **inbound**

SAs are unidirectional.

---

## Internet Key Exchange (IKE)

IKE is responsible for establishing shared keys and negotiating IPsec parameters.  
It runs in **two main phases**.

### **IKE Phase 1**
Purpose: Establish a secure, authenticated channel.  
Outputs:  
- ISAKMP SA  
- Shared keying material  
- Trusted peer identity  

Two methods exist:  
- **Main mode** (more secure, slower)  
- **Aggressive mode** (faster, fewer exchanges)

---

### **IKE Phase 2 (Quick Mode)**
Purpose: Negotiate the actual IPsec SAs used for ESP/AH.  
Outputs:  
- IPsec SA(s)  
- Encryption and integrity parameters  
- Fresh keying material for data protection  

This is the phase that establishes how actual traffic will be encrypted.

---

## Anti-Replay Protection

IPsec includes mechanisms to prevent attackers from reusing captured packets.  
This is achieved through:

- Sequence numbers  
- Sliding replay windows  
- Packet validation rules  

If a packet’s sequence number falls outside the window or is duplicated, it is dropped.

---

## IPsec Packet Flow (ASCII Diagram)

```
+----------------------+       +------------------------+       +----------------------+
|   Host A             | ----> |  IPsec Gateway / VPN   | ----> |       Host B         |
| 192.168.1.10         |       |  Establishes Tunnel    |       | 10.10.0.25           |
+----------------------+       +------------------------+       +----------------------+
             |                            |                               |
             +------ Encrypted Tunnel ----+------ Encrypted Tunnel -------+
```

This represents a typical site-to-site IPsec tunnel, where gateways handle encapsulation and encryption.

---

## Summary

IPsec is a widely used protocol suite for securing IP communication. By providing confidentiality, integrity, authentication, and anti-replay protection, it forms the foundation of many VPN implementations. Understanding ESP vs AH, tunnel vs transport mode, and the IKE negotiation process is essential for network and security professionals working with encrypted communication and secure remote connectivity.

