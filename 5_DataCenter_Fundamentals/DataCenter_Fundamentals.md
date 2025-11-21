# Data Center Fundamentals

This document provides a concise overview of essential concepts required for Data Center Technician roles. It covers physical infrastructure, cabling standards, rack hardware, networking devices, power systems, cooling principles, and operational best practices.

---

## Cabling and Connectors

- Copper cabling types: Cat5e, Cat6, Cat6a  
- Fiber cabling types: Single-mode (OS1/OS2), Multi-mode (OM1–OM4)  
- Common connectors: RJ-45, LC, SC  
- Patch panel usage and cable labeling conventions  
- Proper bend radius and cable management techniques  

---

## Rack Hardware

- Understanding rack units (U): 1U = 1.75 inches  
- Rails, cable management arms, and risers  
- Hot aisle and cold aisle layout  
- Airflow direction and equipment spacing  
- Vertical PDUs and structured cable routing  

---

## Networking Devices

- Roles of switches, routers, and firewalls  
- Access ports vs trunk ports  
- VLAN fundamentals  
- Top-of-Rack (ToR), Middle-of-Row (MoR), and End-of-Row (EoR) configurations  
- Basic IP addressing concepts relevant to data center systems  

---

## Storage Fundamentals

- Differences between NAS and SAN  
- RAID levels:  
  - RAID 0: Striping  
  - RAID 1: Mirroring  
  - RAID 5 and 6: Parity  
  - RAID 10: Mirrored stripes  
- High-level comparison of iSCSI and Fibre Channel  

---

## Power and Cooling

- A/B power feed redundancy  
- UPS systems and PDUs  
- Dual power supplies in servers  
- Basic principles of thermal management  
- Hot and cold aisle containment  

---

## Daily Operations and Safety

- Ticket and change management workflows  
- Standard hardware replacement procedures  
- ESD safety practices  
- Proper lifting techniques  
- Cable routing standards  
- Documentation and labeling requirements  

---

## ASCII: Data Center Rack Diagram

```
+---------------------------------------------------+
|                 Data Center Rack                  |
+---------------------------------------------------+
|                                                   |
|  [ 1U  ]  Patch Panel (Fiber)                     |
|  [ 2U  ]  Patch Panel (Copper)                    |
|  [ 3U  ]---------------------------------------   |
|  [ 4U  ]  Top-of-Rack Switch (ToR)                |
|  [ 5U  ]---------------------------------------   |
|  [ 6U  ]  Server Node 1 (Compute)                 |
|  [ 7U  ]  Server Node 2 (Compute)                 |
|  [ 8U  ]  Server Node 3 (Compute)                 |
|  [ 9U  ]---------------------------------------   |
|  [ 10U ]  Storage Shelf (NAS/SAN)                 |
|  [ 11U ]---------------------------------------   |
|  [ 12U ]  Backup or Security Appliance            |
|  [ 13U ]---------------------------------------   |
|  [ 14U ]  PDU (A-Side)                            |
|  [ 15U ]  PDU (B-Side)                            |
|                                                   |
+---------------------------------------------------+
Legend:
- ToR = Top-of-Rack switch
- PDU = Power Distribution Unit
```

---

## ASCII: Troubleshooting Flowchart

```
+---------------------------------------------------+
|              Data Center Troubleshooting          |
+---------------------------------------------------+

       ┌──────────────────────┐
       │  Issue Detected?     │
       └───────┬──────────────┘
               │ Yes
               ▼
       ┌──────────────────────┐
       │  Identify System     │
       │  Server / Network /  │
       │  Storage / Power     │
       └───────┬──────────────┘
               ▼
       ┌──────────────────────┐
       │  Check Physical      │
       │  - Cable seating     │
       │  - Power LEDs        │
       │  - NIC link lights   │
       └───────┬──────────────┘
               │ If OK
               ▼
       ┌──────────────────────┐
       │  Check Logical Layer │
       │  - IP / VLAN         │
       │  - Switch port state │
       │  - iDRAC / iLO       │
       └───────┬──────────────┘
               │ If still down
               ▼
       ┌──────────────────────┐
       │      Review Logs     │
       │  - Server logs       │
       │  - Switch logs       │
       │  - Storage alerts    │
       └───────┬──────────────┘
               │ If root cause found
               ▼
       ┌──────────────────────┐
       │      Apply Fix       │
       └───────┬──────────────┘
               ▼
       ┌──────────────────────┐
       │ Document in Ticket   │
       └──────────────────────┘
```

---

## Summary

This document provides the foundational knowledge required for Data Center Technician tasks and interviews. It aligns with the technical style used across this repository and presents information clearly, without unnecessary decoration.

