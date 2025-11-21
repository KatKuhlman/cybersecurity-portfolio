# IPv4 Subnetting Overview

This document provides a structured explanation of IPv4 addressing, subnet masks, network and host portions, and how to determine subnet boundaries. It includes an embedded diagram, definitions, and example calculations.

---

## IPv4 Address Structure

An IPv4 address is a 32-bit value divided into four octets:

```
AAA.BBB.CCC.DDD
```

Each octet is 8 bits, for a total of 32 bits:

```
8 bits | 8 bits | 8 bits | 8 bits
```

Example:

```
192.168.100.10
```

Binary representation:

```
11000000.10101000.01100100.00001010
```

---

## Subnet Masks

A subnet mask defines which portion of the IPv4 address is the **network** portion and which is the **host** portion.

Example subnet mask:

```
255.255.255.0
```

Binary:

```
11111111.11111111.11111111.00000000
```

CIDR notation:

```
/24
```

This means:  
- **24 bits** are network bits  
- **8 bits** are host bits  

---

## Network vs Host Portions (Diagram)

Below is the subnetting diagram extracted from the provided image, represented in text so it renders properly in GitHub.

```
+----------------------------------------------------------------+
|               Network Portion               |   Host Portion   |
+----------------------------+----------------+------------------+
|   11000000   |   10101000  |   01100100     |    00001010      |
|     192      |     168     |      100       |       10         |
+----------------------------+----------------+------------------+
          8 bits       8 bits        8 bits         8 bits
```

This diagram shows how an IPv4 address is separated into sections according to the subnet mask.

---

## Determining Network and Broadcast Addresses

Given:

```
IP Address: 192.168.100.10
Subnet Mask: 255.255.255.0 (/24)
```

### Network Address

To find the network address:

- Copy all **network bits**
- Zero out all **host bits**

```
192.168.100.0
```

### Broadcast Address

To find the broadcast address:

- Copy all network bits
- Set all host bits to **1**

```
192.168.100.255
```

---

## Usable Host Range

For a /24 network:

- First usable: `192.168.100.1`
- Last usable:  `192.168.100.254`

Total usable hosts:

```
2^(32-24) - 2 = 254 hosts
```

---

## CIDR Examples

### /25

```
Subnet Mask: 255.255.255.128
Network Portion: 25 bits
Host Portion: 7 bits
Usable Hosts: 2^7 - 2 = 126
```

### /26

```
Subnet Mask: 255.255.255.192
Network Portion: 26 bits
Host Portion: 6 bits
Usable Hosts: 2^6 - 2 = 62
```

### /30 (common for router links)

```
Subnet Mask: 255.255.255.252
Network Portion: 30 bits
Host Portion: 2 bits
Usable Hosts: 2 (point-to-point)
```

---

## Subnetting Calculation Workflow

1. Determine CIDR mask  
2. Calculate number of host bits  
3. Compute total usable hosts  
4. Determine block size  
5. Identify network boundaries  
6. Determine network address  
7. Determine broadcast address  
8. Determine usable range  

Example:

```
CIDR: /26
Block Size: 64
Network ranges:
0–63
64–127
128–191
192–255
```

Given an IP:

```
192.168.100.130
```

It falls into the **128–191** block:

- Network: `192.168.100.128`
- Broadcast: `192.168.100.191`
- Usable range: `192.168.100.129 – 192.168.100.190`

---

## Summary

This document provides a clear overview of IPv4 addressing and subnetting concepts, including network vs host portions, CIDR notation, block sizes, and how to calculate network and broadcast addresses. These fundamentals are essential for troubleshooting, routing, security analysis, and understanding packet flow within any network environment.

