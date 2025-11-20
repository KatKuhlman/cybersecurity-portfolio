# Wireshark Display Filters & Traffic Analysis Reference

Wireshark is a core tool for cybersecurity analysts. Display filters allow you to isolate packets, investigate alerts, and understand network behavior quickly. This page summarizes commonly used filters, when to apply them, and short analysis examples you can replicate in a home lab.

---

## Overview

This reference covers:

- Essential Wireshark display filters  
- Protocol-based filters  
- Investigation-focused filters  
- Practical examples for a home lab  
- A quick-reference table  

---

# 1. Essential Filters

### **Filter: `ip.addr == x.x.x.x`**  
Shows all traffic to or from a specific IP address.

**Use cases:** device scoping, suspicious communication, east/west movement.

---

### **Filter: `tcp.port == 80`**  
Shows packets on a specific TCP port.

**Use cases:** investigating service behavior, analyzing clear-text traffic.

---

### **Filter: `http`**  
Displays HTTP traffic.

**Use cases:** reviewing web requests, analyzing insecure logins.

---

### **Filter: `dns`**  
Shows DNS queries and responses.

**Use cases:** suspicious domains, C2 behavior, typosquatting.

---

# 2. Protocol-Specific Filters

### Common Network Protocols

| Filter | Purpose |
|--------|---------|
| `tcp` | All TCP packets |
| `udp` | All UDP packets |
| `icmp` | Ping and diagnostic traffic |
| `tls` | Encrypted TLS traffic |
| `ftp` | FTP sessions (clear-text) |
| `ssh` | Encrypted remote shell traffic |

---

### Email & Authentication Protocols

| Filter | Purpose |
|--------|---------|
| `smtp` | Outbound email |
| `imap` | Email retrieval |
| `pop3` | Legacy email retrieval |
| `kerberos` | Windows authentication |
| `ntlmssp` | NTLM authentication traffic |

---

# 3. Investigation-Focused Filters

These filters are commonly used in SOC investigations and IR workflows.

---

### **Filter: `tcp.flags.syn == 1 && tcp.flags.ack == 0`**  
Shows SYN packets that initiate connections.

**Use cases:** port scans, connection attempts, recon activity.

---

### **Filter: `tcp.analysis.retransmission`**  
Displays retransmitted packets.

**Use cases:** troubleshooting network issues, identifying packet loss.

---

### **Filter: `frame contains "password"`**  
Searches packet payloads for a string.

**Use cases:**  
Home lab testing only — confirms clear-text credential exposure.

---

### **Filter: `dns.qry.name contains ".xyz"`**  
Shows DNS queries for a specific TLD.

**Use cases:** tracking unusual TLD lookups, malware behavior.

---

# 4. Quick Analysis Scenarios (Home Lab Friendly)

These scenarios demonstrate real-world packet analysis skills.

---

### Scenario A — Detect a Basic Port Scan  
**Filter:**  
```
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

**Expected pattern:**  
Repeated SYN packets to many ports from the same source.

---

### Scenario B — Identify Clear-Text Credentials  
**Filters:**  
```
http.request.method == "POST"
frame contains "username"
```

**Expected pattern:**  
Form submissions or visible credentials in clear-text.

---

### Scenario C — Investigate Suspicious DNS Behavior  
**Filter:**  
```
dns
dns.qry.name contains "amazonaws"
```

**Expected pattern:**  
High-frequency DNS lookups, possible C2 traffic.

---

# 5. Quick Reference Table

```
+---------------------------+--------------------------------------------+
| Filter                    | Description                                |
+---------------------------+--------------------------------------------+
| ip.addr == x.x.x.x        | All traffic to/from an IP                  |
| tcp.port == 80            | Traffic on TCP port 80                     |
| udp.port == 53            | DNS (UDP) traffic                          |
| http                      | All HTTP packets                           |
| dns                       | DNS queries and responses                  |
| tls                       | TLS handshake & encrypted traffic          |
| icmp                      | Ping / diagnostic packets                  |
| ftp                       | FTP traffic (clear-text)                   |
| tcp.flags.syn == 1        | SYN packets (scan/recon indicator)         |
| frame contains "string"   | Search payloads for specified text         |
+---------------------------+--------------------------------------------+
```

---

# Summary

This document provides a clean, hybrid-level overview of Wireshark display filters and basic packet analysis techniques. These examples can be expanded later with screenshots, PCAPs, or walkthroughs from lab work and TryHackMe exercises.

