# Wireshark Display Filters

This document provides a reference for commonly used Wireshark display filters. These filters help narrow traffic during packet analysis, troubleshooting, and SOC investigations.

---

## 1. Filtering by IP Address

### Single IP (source or destination)
ip.addr == 192.168.1.10

### Source IP only
ip.src == 192.168.1.10

### Destination IP only
ip.dst == 192.168.1.10

### Exclude an IP
!(ip.addr == 192.168.1.1)

---

## 2. Filtering by Protocol

### Common protocol filters
http
dns
tcp
udp
icmp
tls

### Combine protocol and IP
http && ip.addr == 10.0.0.15

---

## 3. Filtering by Port

### TCP port
tcp.port == 80

### UDP port
udp.port == 53

### Source port
tcp.srcport == 443

### Destination port
tcp.dstport == 22

---

## 4. HTTP Filters

### HTTP GET requests
http.request.method == "GET"

### HTTP POST requests
http.request.method == "POST"

### Filter for a specific host header
http.host == "example.com"

### User-Agent field contains a string
http.user_agent contains "Mozilla"

---

## 5. DNS Filters

### All DNS traffic
dns

### DNS query name contains a string
dns.qry.name contains "google.com"

### DNS response errors
dns.flags.rcode != 0

---

## 6. TCP Filters

### Show packets with retransmissions
tcp.analysis.retransmission

### Show TCP resets
tcp.flags.reset == 1

### Show SYN packets (start of handshake)
tcp.flags.syn == 1

### Show SYN/ACK packets
tcp.flags.syn == 1 && tcp.flags.ack == 1

---

## 7. Error and Warning Filters

### Malformed packets
malformed

### TCP checksum errors
tcp.checksum_bad == 1

### TLS handshake failures
tls.handshake && tls.record.content_type == 21

---

## 8. SOC Investigation Examples

### 1. Filter all traffic from a suspicious internal host
ip.addr == 10.0.5.23

### 2. Look for failed DNS lookups from that host
dns.flags.rcode != 0 && ip.addr == 10.0.5.23

### 3. Filter for unusual outbound connections (non-443, non-80)
tcp.dstport != 80 && tcp.dstport != 443 && tcp

### 4. Detect possible C2 beaconing by filtering periodic small packets
frame.len < 100 && tcp

### 5. Filter failed TLS handshakes from the same host
tls.record.content_type == 21 && ip.addr == 10.0.5.23

---

## 9. Quick Reference Table

| Purpose               | Filter                             |
|-----------------------|------------------------------------|
| Any traffic for an IP | `ip.addr == X.X.X.X`               |
| DNS queries           | `dns.qry.name contains "example"`  |
| HTTP GET              | `http.request.method == "GET"`     |
| HTTPS/TLS             | `tls`                              |
| Failed DNS lookup     | `dns.flags.rcode != 0`             |
| TCP retransmissions   | `tcp.analysis.retransmission`      |
| Packet length filter  | `frame.len > 500`                  |
| Exclude noisy traffic | `!(ip.addr == X.X.X.X)`            |

---

## Summary

These filters provide a foundation for targeted packet analysis in SOC workflows, incident investigations, and network troubleshooting. They can be combined to narrow traffic to specific hosts, protocols, or behaviors.
