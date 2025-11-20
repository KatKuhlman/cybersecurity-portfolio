# OSI Model Overview

The OSI (Open Systems Interconnection) model is a 7-layer framework that explains how data moves across a network.
Each layer handles specific responsibilities, and together they help describe communication from the physical wire all the way up to the applications we use every day.

Below is a brief description of each layer and its role in network communication.

## The Seven Layers
### 1. Physical Layer

The foundation of all networking.
Handles the actual hardware and transmission of electrical or optical signals.

**Examples:** Ethernet cables, Wi-Fi signals, fiber optics, hubs, repeaters.

### 2. Data Link Layer

Responsible for reliable point-to-point communication on the same local network segment.
Uses MAC addresses to move frames between devices.

**Examples:** Switches, bridges, ARP, PPP.

### 3. Network Layer

Routes packets across different networks.
This is where logical addressing (IP addresses) and routing decisions happen.

**Examples:** IP, ICMP, IPSec, routers.

### 4. Transport Layer

Deals with end-to-end communication and reliability.
Controls flow, error recovery, and segmentation.

**Examples:** TCP, UDP, ports.

### 5. Session Layer

Manages sessions between systems — setting them up, maintaining them, and tearing them down.

**Examples:** APIs, sockets, RPC, NetBIOS.

### 6. Presentation Layer

Translates, formats, or encrypts data so applications can use it properly.

**Examples:** SSL/TLS, data encoding, compression, JPEG, MPEG.

### 7. Application Layer

Where the user interacts with network services.

**Examples:** HTTP, DNS, SSH, FTP, SMTP, IRC.

## OSI Model Table

```
| Layer | Name         | Purpose                                     | Examples             |
|-------|--------------|---------------------------------------------|----------------------|
|   7   | Application  | User-facing services                        | HTTP, DNS, SSH       |
|   6   | Presentation | Data translation, encryption                | TLS, SSL, JPEG       |
|   5   | Session      | Session setup, management, teardown         | Sockets, APIs        |
|   4   | Transport    | End-to-end communication                    | TCP, UDP             |
|   3   | Network      | Routing and logical addressing              | IP, ICMP             |
|   2   | Data Link    | MAC-level communication on local segment    | Switches, ARP        |
|   1   | Physical     | Physical transmission of bits               | Cables, Wi-Fi        |
```

## OSI Model Diagram

```
+---------------------+
|   7. Application    |
+---------------------+
|   6. Presentation   |
+---------------------+
|   5. Session        |
+---------------------+
|   4. Transport      |
+---------------------+
|   3. Network        |
+---------------------+
|   2. Data Link      |
+---------------------+
|   1. Physical       |
+---------------------+
```

## Summary

The OSI model provides a structured way to understand how data moves across a network. 
Knowing the purpose of each layer makes troubleshooting, packet analysis, and network design 
much easier. This model is also foundational knowledge for roles such as SOC Analyst, 
Cybersecurity Analyst, and Network Technician.
