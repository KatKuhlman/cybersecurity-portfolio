# Home Lab Setup

This folder documents my cybersecurity home lab environment used for hands-on learning, safe testing, and practicing SOC and blue-team concepts.

## 🖥 Lab Overview
The lab is built around an isolated test network that includes:

- **Kali Linux (attacker VM)**
- **Xubuntu or Windows (victim VM)**
- **VirtualBox or VMware Workstation**
- **Managed switch + CAT6 cabling**
- **Dedicated subnet for testing** (separate from home network)
- **Local workstation used as the controller/analyst machine**

This setup allows me to safely simulate attacks, monitor network behavior, and practice detection and response workflows.

---

## 🛠 What This Lab Is Used For

### **🔍 Network Scanning & Recon**
- Nmap scanning
- Service and OS enumeration
- Understanding open ports, protocols, and services

### **📡 Traffic Capture & Analysis**
- Packet capture using **Wireshark**
- Investigating suspicious traffic
- Understanding normal vs abnormal behavior

### **🛡 SOC & Defensive Practice**
- Windows Event Log and Sysmon analysis
- Testing SIEM-like workflows (Wazuh, Splunk Free, or ELK Stack)
- Observing attack patterns and log artifacts

### **⚔️ Safe Offensive Testing**
- Brute forcing basics (Hydra)
- Web vulnerability exploration (beginner-level)
- Linux privilege escalation labs
- Testing payloads in a controlled environment

---

## 📚 Documentation Included
This folder will contain:

- Network diagrams  
- VM installation and configuration steps  
- Switch and subnet settings  
- Notes on isolation and safe lab practices  
- Packet capture examples  
- Lab scenarios and findings  

This lab is actively updated as I continue building hands-on skills in cybersecurity fundamentals, blue-team workflows, and introductory offensive security techniques.
