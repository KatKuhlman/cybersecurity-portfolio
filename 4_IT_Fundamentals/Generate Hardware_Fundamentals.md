# Hardware Fundamentals

This document provides an overview of core computer hardware concepts that support modern IT, cybersecurity, data center operations, and general system administration.  
It covers the components, standards, and troubleshooting methodologies essential for foundational technical roles.

---

## 1. Central Processing Unit (CPU)

The CPU executes instructions and manages system operations.

### Key Concepts
- **Cores**: Independent processing units within the CPU.  
- **Threads**: Virtual or logical execution paths (SMT/Hyper-Threading).  
- **Clock Speed**: Frequency (GHz) representing operations per second.  
- **Architecture**: x86_64 for most desktops/servers; ARM for mobile and some servers.  
- **Cache Levels**:
  - L1: Fastest, smallest  
  - L2: Intermediate  
  - L3: Largest, shared  

### CPU Bottlenecks
- High CPU utilization  
- Single-threaded workload saturation  
- Thermal throttling  
- Poor cooling or inadequate airflow  

---

## 2. Memory (RAM)

RAM temporarily stores data the CPU needs to access quickly.

### RAM Characteristics
- **DDR Generations**: DDR3, DDR4, DDR5 (not interchangeable)  
- **Speed**: Measured in MT/s, affects bandwidth  
- **Latency**: Lower latency allows faster access  
- **Channel Configuration**:
  - Single-channel  
  - Dual-channel  
  - Quad-channel (servers/workstations)  
- **ECC vs Non-ECC**:
  - ECC: Error-correcting; used in servers  
  - Non-ECC: Common in desktops  

### Symptoms of RAM Issues
- Random reboots  
- Blue screens or kernel panics  
- Application crashes  
- Failed POST beeps  

---

## 3. Storage Devices

### Types of Storage

#### HDD (Hard Disk Drive)
- Magnetic platters  
- High capacity  
- Slowest performance  
- Mechanical failure risk  

#### SATA SSD
- Solid-state storage, no moving parts  
- Faster than HDD  
- Limited by SATA interface speed  

#### NVMe SSD
- Uses PCIe lanes  
- Much faster throughput and lower latency  
- Ideal for OS drives, virtualization, high-speed workloads  

### Key Metrics
- IOPS (I/O operations per second)  
- Throughput (MB/s)  
- Latency  
- TBW (terabytes written) for SSD endurance  

---

## 4. Motherboards and Chipsets

The motherboard connects and integrates all system components.

### Components
- CPU socket  
- RAM slots  
- PCIe slots  
- Storage connectors (SATA, M.2)  
- Power connectors (ATX/EPS)  
- Chipset for I/O control  

### Chipset Features
- Determines available PCIe lanes  
- Controls USB ports and onboard features  
- Defines overclocking support  
- Manages storage and I/O pathways  

---

## 5. Power Supply Units (PSU)

The PSU converts AC mains power to regulated DC voltages for system components.

### PSU Characteristics
- **Wattage**: Total available power  
- **Efficiency Rating**:
  - 80 Plus  
  - Bronze / Silver / Gold / Platinum  
- **Rails**:
  - Single-rail: Higher amperage on one 12V rail  
  - Multi-rail: Separate 12V outputs  

### PSU Issues
- Unexpected shutdowns under load  
- Voltage instability  
- System failing to power on  

---

## 6. Graphics Processing Unit (GPU)

GPUs accelerate graphic rendering and parallel computations.

### GPU Roles
- Gaming and graphics workloads  
- CUDA/OpenCL compute tasks  
- AI and machine learning processing  
- Video rendering  

### GPU Connections
- PCIe x16 slot  
- Auxiliary power connectors (6-pin, 8-pin)  

### GPU Issues
- Artifacts on screen  
- Driver crashes  
- Overheating under load  

---

## 7. BIOS and UEFI

Firmware that initializes hardware and starts the OS.

### Key Tasks
- Power-On Self Test (POST)  
- Loading system bootloader  
- Configuring hardware features  
- Enabling virtualization support  

### POST Example (ASCII)

```
+------------------------+
| Power On               |
+------------------------+
| POST: CPU Check        |
| POST: RAM Check        |
| POST: GPU Check        |
+------------------------+
| Bootloader Loaded      |
+------------------------+
| Operating System Loads |
+------------------------+
```

---

## 8. Peripheral Buses

### PCI Express (PCIe)
- High-speed interface for GPUs, NVMe SSDs, NICs  
- Lane configurations: x1, x4, x8, x16  
- PCIe generations: 3.0, 4.0, 5.0  

### SATA
- 6 Gbps limit  
- Used for HDDs and some SSDs  

### USB Standards
- USB 2.0 (480 Mbps)  
- USB 3.0/3.1 Gen 1 (5 Gbps)  
- USB 3.2/3.1 Gen 2 (10 Gbps)  
- USB4 / Thunderbolt 3-4 (40 Gbps)  

---

## 9. Hardware Monitoring & Management

### Tools
- **Windows**: Task Manager, Resource Monitor, Event Viewer  
- **Linux**: `top`, `htop`, `lsblk`, `dmesg`, `lspci`  
- **Firmware Tools**:
  - SMART tests for storage  
  - Temperature sensors  
  - Fan controllers  

---

## 10. Hardware Troubleshooting Workflow

1. Identify symptoms
2. Check physical connections
3. Review logs or POST messages
4. Swap or reseat components
5. Test with known-good hardware
6. Verify resolution
7. Document results

### Common Hardware Issue Symptoms
- **RAM**: crashing apps, BSOD  
- **CPU**: overheating, slow processing  
- **GPU**: visual artifacts  
- **PSU**: random shutdowns  
- **Storage**: slow I/O, clicking noises (HDD)  

---

## 11. ESD (Electrostatic Discharge) Precautions

- Use a grounded wrist strap  
- Avoid working on carpet  
- Handle hardware by the edges  
- Store components in anti-static bags  
- Touch grounded metal before handling parts  

---

## Summary

This document outlines foundational hardware concepts including CPU, RAM, storage, power supplies, chipsets, firmware, buses, and troubleshooting processes.  
Understanding these components is essential for entry-level cybersecurity, SOC roles, help desk, and data center operations.
