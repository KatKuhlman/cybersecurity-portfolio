# Offline Brute Force Attacks on Hashes

## Overview
This lab demonstrated how adversaries recover plaintext credentials by performing offline brute-force attacks against NTLM password hashes. By analyzing extracted hash data and running controlled recovery attempts, the exercise highlighted the risks associated with weak password hygiene, unsalted hashing algorithms, and credential exposure during system compromise.

## Platform & Environment
- IronCircle — UNLV Cybersecurity Bootcamp Hosted Lab
- Linux terminal (Konsole)
- hashcat (offline password recovery tool)
- NTLM hash samples provided within the lab dataset

## Skills Demonstrated
- Hash identification and analysis
- Conducting offline brute-force and dictionary-based attacks
- Evaluating password strength and entropy
- Researching and selecting appropriate attack modes for NTLM
- Understanding credential exploitation techniques used in real intrusions

## Methodology
1. Reviewed the provided password hash file and verified NTLM formatting.
2. Identified the correct hash type and corresponding hashcat mode for NTLM attacks.
3. Executed an offline brute-force recovery attempt using hashcat against the target hashes.
4. Monitored the cracking process, analyzed recovered credentials, and validated password accuracy.
5. Evaluated why the cracked passwords were vulnerable and how adversaries leverage exposed hashes after credential dumping.

## Key Findings
- NTLM hashing is computationally fast and unsalted, making it highly susceptible to brute-force and dictionary attacks.
- Weak, short, or predictable passwords were cracked with minimal effort.
- Offline attacks do not interact with authentication systems, bypassing account lockouts, SIEM alerts, and monitoring controls.
- Once hashed credentials are exfiltrated, defenders have limited visibility into attacker cracking activity.

## Real-World Impact
Offline brute-force attacks typically occur after credential dumping events involving tools such as Mimikatz, LSASS memory extraction, SAM database access, or database breaches. Attackers can recover passwords on their own hardware, reuse cracked credentials for lateral movement, escalate privileges, or authenticate into cloud or on-prem environments without generating traditional login telemetry.

## MITRE ATT&CK Mapping
**T1110.002 — Brute Force: Offline**  
Attackers obtain credential material and attempt password recovery without interacting with live authentication systems.

## Mitigation & Best Practices

### Credential Hardening
- Enforce long, complex password policies.
- Implement modern, GPU-resistant hashing algorithms (bcrypt, scrypt, PBKDF2, Argon2).
- Minimize or disable NTLM authentication where possible.

### System Protection
- Enable Credential Guard or LSA protection to prevent unauthorized hash extraction.
- Limit local administrator privileges and restrict lateral movement pathways.
- Monitor high-risk actions such as LSASS access attempts, SAM file reads, and credential dumping behavior.

### Operational Controls
- Treat password hashes as sensitive data equivalent to plaintext credentials.
- Rotate privileged credentials frequently.
- Use MFA wherever possible to reduce damage from cracked passwords.

## Reflection
This lab reinforced how quickly NTLM hashes can be cracked once exposed and why credential dumping remains a high-value technique for adversaries. Understanding offline brute-force methods provides insight into attacker workflows and supports stronger defensive measures around password policy, authentication design, and endpoint hardening.
