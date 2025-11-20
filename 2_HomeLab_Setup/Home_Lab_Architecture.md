# Home Lab Architecture & Network Setup

This document explains the structure, purpose, and configuration of my cybersecurity home lab.  
The goal of this environment is to provide a safe, isolated space for practicing network analysis, blue-team workflows, and beginner offensive security techniques.

The lab follows industry best practices for segmentation, logging, and safe experimentation.

---

## Objectives of the Home Lab

- Build a safe environment for hands-on cybersecurity learning  
- Practice both defensive (SOC) and offensive techniques  
- Understand how real attacks unfold inside a network  
- Capture and analyze network traffic using Wireshark  
- Explore virtual machine networking, segmentation, and isolation  
- Develop documentation skills used in entry-level analyst roles  

---

## High-Level Architecture

The home lab uses **VirtualBox** or **VMware Workstation**, one physical workstation, and a small isolated test network.

```
+-------------------------------------------------------------+
|                     Home Lab Environment                    |
+-------------------------------------------------------------+
|                                                             |
|   [Analyst Workstation]                                     |
|        (Host OS: Wireshark, Notes, Browser)                 |
|                         |                                   |
|                         | Host-only / Internal Network      |
|                         v                                   |
|   +-----------------------------------------------+         |
|   |            Internal Test Network             |          |
|   |                                              |          |
|   |   [Kali VM]   <----->   [Victim VM (Linux)]  |          |
|   |                       \                      |          |
|   |                        \--> [Victim VM (Win)]           |
|   +-----------------------------------------------+         |
|                                                             |
+-------------------------------------------------------------+
```

### Key features of this design:

- The attacker and victim machines are on an **isolated network**  
- The analyst workstation can monitor traffic without exposing the home network  
- Virtual machines cannot reach the internet unless explicitly allowed  
- Network activity is predictable and controlled  

---

## Virtualization Configuration

### **VirtualBox / VMware Settings**

**Network Adapter Types:**

| Mode             | Purpose                                   | Security Notes                       |
|------------------|-------------------------------------------|--------------------------------------|
| NAT              | Allows outbound internet access           | Used only when updates are required  |
| Bridged          | VM acts like a device on the home network | *Disabled for security*              |
| Host-only        | VM can talk to host only                  | Used for analysis and SOC practice   |
| Internal Network | VMs talk only to each other               | Used for attack simulations          |


### Recommended Setup

- **Kali VM** → Internal Network  
- **Victim VM(s)** → Internal Network  
- **Analyst Workstation** → Host-only + Internal Network  

### This allows:

- Traffic capture from analyst workstation  
- Attack simulations between Kali & victim machines  
- Zero exposure to the home Wi-Fi or other devices  

---

## Logical Network Diagram

```
                    [Analyst Workstation]
                       (Host-only NIC)
                             |
                             |
                +---------------------------+
                |   Internal Test Network   |
                +---------------------------+
                    |                  |
                    |                  |
              [Kali VM]         [Victim VM(s)]
         (Attacker / Tools)   (Linux / Windows)
```

---

## Purpose of Each Component

### **Analyst Workstation**
- Runs Wireshark for packet analysis  
- Used for documentation, screenshots, and reporting  
- Acts as the “SOC analyst perspective”  
- Never directly participates in the attack  

### **Kali Linux VM**
- Used for reconnaissance, scanning, and exploitation practice  
- Helps understand what attacker traffic looks like in logs and on the wire  
- Generates artifacts that can later be analyzed defensively  

### **Victim Machines (Windows & Linux)**
Used for:

- Observing artifacts from attacks  
- Investigating system logs  
- Practicing privilege escalation concepts  
- Checking Windows Event Logs and Sysmon traces  
- Identifying persistence techniques  

---

## Lab Use Cases

### **1. Network Scanning & Recon**
- Nmap host discovery  
- Service enumeration  
- Fingerprinting systems  
- Understanding normal vs suspicious ports  

### **2. Traffic Capture & Analysis**
- Capture packets using Wireshark  
- Analyze TCP handshakes, DNS queries, HTTP traffic  
- Identify unusual patterns and possible malicious behavior  
- Compare normal system activity vs attack traffic  

### **3. Windows Event Log & Sysmon Practice**
- Review Security logs  
- Track process creation events  
- Investigate failed logins, RDP attempts, privilege escalation behavior  

### **4. Linux Security Practice**
- Review /var/log/auth.log  
- Monitor SSH attempts  
- Practice reading system logs and identifying changes  

### **5. Beginner Offensive Security**
- Safe password attacks  
- Enumerating open ports and services  
- Simple web vulnerability exploration  
- Understanding how exploits generate detectable artifacts  

---

## Lab Safety & Isolation

Security precautions:

- No VM is bridged to the home network  
- No malware or dangerous payloads are used  
- Internal network has **no internet access** unless updating tools  
- Strong host OS firewall settings  
- No sensitive or personal data stored in the lab VMs  

These practices mirror professional lab setups used in training and certifications.

---

## How This Lab Supports SOC Skills

- Identifying suspicious traffic patterns  
- Correlating attacker behavior with system logs  
- Reproducing alerts in a controlled environment  
- Building investigation notes and incident timelines  
- Improving familiarity with network protocols and port usage  

---

## Summary

This home lab provides a controlled environment for learning both foundational networking skills and real-world cybersecurity concepts.  
By working with isolated VMs, monitoring traffic, analyzing logs, and documenting findings, I can safely practice the same workflows used by SOC analysts, cybersecurity analysts, and junior penetration testers.
