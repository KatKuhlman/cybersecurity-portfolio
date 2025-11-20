# Common Network Ports Reference

Understanding well-known network ports is essential for troubleshooting, packet analysis, SOC work, and identifying suspicious behavior on a network.  
This reference summarizes the most important ports a cybersecurity analyst should know, along with why they matter from a defensive perspective.

---

## Why Ports Matter

Ports act as communication endpoints that allow devices and applications to talk to one another.  
Because attackers also rely on these ports to find weaknesses, knowing what each port represents helps analysts spot unusual or unauthorized activity.

---

## Most Common Ports and Their Security Relevance

Below is a concise table of high-value ports.  
These are the ports most frequently seen in SOC alerts, investigations, and malicious activity.

```
| Port    | Protocol | Service Name           | Security Notes                                     |
| ------- | -------- | ---------------------- | -------------------------------------------------- |
| 20/21   | TCP      | FTP                    | Cleartext credentials; often brute-forced          |
| 22      | TCP      | SSH                    | Secure remote access; frequent target for attacks  |
| 23      | TCP      | Telnet                 | Insecure; cleartext; should not be used            |
| 25      | TCP      | SMTP                   | Email relay; spam/phishing vector                  |
| 53      | UDP/TCP  | DNS                    | DNS tunneling, domain spoofing, command & control  |
| 67/68   | UDP      | DHCP                   | Rogue DHCP servers, network spoofing               |
| 69      | UDP      | TFTP                   | No authentication; used in attacks/worms           |
| 80      | TCP      | HTTP                   | Unencrypted web traffic; web attacks common        |
| 110     | TCP      | POP3                   | Email retrieval; often insecure                    |
| 123     | UDP      | NTP                    | Used in DDoS amplification attacks                 |
| 137-139 | TCP/UDP  | NetBIOS                | Older Windows services; lateral movement risks     |
| 143     | TCP      | IMAP                   | Email protocol; may be unencrypted                 |
| 161/162 | UDP      | SNMP                   | Device enumeration; weak default community strings |
| 389     | TCP/UDP  | LDAP                   | Directory services; exploited for enumeration      |
| 443     | TCP      | HTTPS                  | Encrypted web; hides malicious traffic             |
| 445     | TCP      | SMB                    | Used in ransomware and lateral movement            |
| 514     | UDP      | Syslog                 | Log transport; can be spoofed                      |
| 587     | TCP      | SMTP (Auth)            | Secure email submission                            |
| 636     | TCP      | LDAPS                  | Encrypted directory access                         |
| 989/990 | TCP      | FTPS                   | Encrypted FTP                                      |
| 993     | TCP      | IMAPS                  | Encrypted IMAP                                     |
| 995     | TCP      | POP3S                  | Encrypted POP3                                     |
| 3306    | TCP      | MySQL                  | Database server; high-value target                 |
| 3389    | TCP      | RDP                    | Remote Desktop; heavily exploited for intrusion    |
| 5432    | TCP      | PostgreSQL             | Database port; sensitive data                      |
| 5900    | TCP      | VNC                    | Remote desktop; sometimes misconfigured            |
| 6379    | TCP      | Redis                  | No auth by default; remote exploitation risks      |
| 8080    | TCP      | HTTP Alternate/Proxies | Often used by web apps and C2 servers              |
```

---

## Notes on High-Risk Ports

### **22 – SSH**
Often hammered by brute-force attacks.  
Look for repeated login attempts from the same IP or odd usernames.

### **23 – Telnet**
Unencrypted and obsolete.  
Any use is suspicious and should trigger an alert.

### **53 – DNS**
A common channel for:
- Tunneling  
- Data exfiltration  
- Malware command-and-control  

Unusual long TXT records or large volumes of outbound DNS traffic are red flags.

### **80 / 443 – HTTP / HTTPS**
Nearly all web attacks begin here:  
SQL injection, XSS, directory traversal, brute force, credential stuffing.

Encrypted HTTPS can hide malicious payloads from casual inspection.

### **445 – SMB**
Infamous for:
- EternalBlue  
- Worm propagation  
- Internal lateral movement  
- Ransomware  

Any external exposure of this port is a critical vulnerability.

### **3389 – RDP**
One of the most abused ports in cybersecurity.  
Common attack types:
- Credential stuffing  
- Bruteforce  
- BlueKeep-style exploits  
- Unauthorized remote access attempts  

Should never be exposed directly to the internet.

---

## Summary

Knowing the purpose of commonly used ports helps analysts:
- Identify anomalies in packet captures  
- Understand SIEM alerts  
- Recognize early indicators of compromise  
- Harden network configurations  
- Detect brute-force, scanning, and lateral movement attempts  

This reference provides a quick overview of the ports most frequently involved in both legitimate network activity and cyber attacks.
