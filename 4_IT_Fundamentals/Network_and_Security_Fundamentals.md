# Network and Security Fundamentals

This document provides essential IT knowledge that supports networking, SOC analysis, home lab environments, data center work, and general system administration.  
It consolidates baseline concepts required for entry-level cybersecurity and infrastructure roles.

---

## 1. Networking Device Roles

Understanding core network devices is foundational to interpreting traffic, troubleshooting connectivity, and building secure architectures.

### Router
- Connects multiple networks
- Performs routing and forwarding based on IP addresses
- Typically used at network edges or gateways
- Can implement NAT, DHCP, ACLs

### Switch
- Connects devices within the same network (LAN)
- Operates at Layer 2 using MAC addresses
- Creates separate collision domains per port
- VLAN support separates broadcast domains

### Firewall
- Enforces security policies based on rules
- Filters traffic using ports, IPs, protocols, and zones
- Can operate in routed or transparent mode
- May include IDS/IPS functionality

---

## 2. SOAR and Playbooks

### SOAR (Security Orchestration, Automation, and Response)
A SOAR platform centralizes alerts, automates repetitive tasks, and provides structured incident handling.

Key capabilities:
- Alert enrichment  
- Automated responses (isolating hosts, disabling accounts)  
- Case management and reporting  
- Workflow orchestration across tools  

### Incident Playbooks
A playbook provides a consistent response process for a specific type of incident.

Typical playbook sections:
1. Trigger condition  
2. Identification and triage steps  
3. Containment actions  
4. Eradication and recovery procedures  
5. Documentation requirements  
6. Lessons learned  

Playbooks ensure repeatable, defensible actions during incidents.

---

## 3. Uptime and Downtime Calculations

Availability is measured as:
Availability (%) = (Total Time − Downtime) / Total Time × 100

Example:
- Total time in a year: 525,600 minutes  
- Suppose downtime: 60 minutes  
(525600 − 60) / 525600 × 100 = 99.9886%

Common SLA tiers:
- 99% (“two nines”) → ~87 hours downtime/year  
- 99.9% (“three nines”) → ~8.7 hours  
- 99.99% (“four nines”) → ~52 minutes  
- 99.999% (“five nines”) → ~5 minutes  

---

## 4. OS Concepts and System Files

### Hosts File
Used for local DNS overrides.

Locations:
- Windows: `C:\Windows\System32\drivers\etc\hosts`
- Linux: `/etc/hosts`
- macOS: `/etc/hosts`

### Process and Service Basics
- A **process** is a running program instance.
- A **service** (daemon) is a background process started at boot or on demand.
- Services are managed differently depending on OS:
  - Windows: `services.msc`, `sc`, PowerShell cmdlets  
  - Linux: `systemctl`, `service`, init scripts  

---

## 5. Security Concepts

### CIA Triad
- **Confidentiality** – preventing unauthorized access  
- **Integrity** – ensuring data is accurate and unaltered  
- **Availability** – ensuring access when needed  

### Defense-in-Depth
Multiple layered controls such as:
- Physical security  
- Network segmentation  
- Firewalls  
- Endpoint protection  
- Monitoring and detection  
- Access controls  
- Backup and recovery  

### Principle of Least Privilege
Users and processes should only have the permissions necessary to perform their tasks.

---

## 6. Network Architecture Fundamentals

### IP Addressing
IPv4 uses a 32-bit dotted-decimal format:
`192.168.1.10`

### Subnet Mask
Defines network vs host bits:
`255.255.255.0` → /24

### VLANs
Segment a network into isolated broadcast domains.

Example:
- VLAN 10: Workstations  
- VLAN 20: Servers  
- VLAN 30: VoIP  
- VLAN 99: Management  

### Access vs Trunk Ports
- **Access port**: carries a single VLAN  
- **Trunk port**: carries multiple VLANs using tagging  

---

## 7. Basic Troubleshooting Workflow

A common approach used by help desk, SOC teams, and data center technicians:

1. Identify the problem
2. Establish a theory
3. Test the theory
4. Define the root cause
5. Implement a solution
6. Verify full functionality
7. Document the findings

This structure applies to network, endpoint, and application troubleshooting alike.

---

## 8. Common Protocols and Their Purposes

| Protocol | Port | Description              |
|---------|------|---------------------------|
| HTTP    | 80   | Web traffic (unencrypted) |
| HTTPS   | 443  | Secure web traffic        |
| DNS     | 53   | Domain name resolution    |
| DHCP    | 67/68| Dynamic IP assignment     |
| SSH     | 22   | Secure remote access      |
| RDP     | 3389 | Remote desktop (Windows)  |

---

## 9. Basic Layered Diagram (Conceptual Stack)

+-------------------------+
| Applications            |
+-------------------------+
| Operating System        |
+-------------------------+
| Network Stack           |
+-------------------------+
| Hardware Interfaces     |
+-------------------------+
| Physical Hardware       |
+-------------------------+

This simplified view helps frame where issues occur when troubleshooting.

---

## Summary

This document consolidates essential IT, networking, and security concepts into a single reference.  
It supports all other sections of the portfolio by providing a strong technical baseline that applies across cybersecurity, SOC analysis, help desk, and data center technician roles.
