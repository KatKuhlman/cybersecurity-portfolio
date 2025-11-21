# Email Header Analysis

This document explains the structure and purpose of email headers, how to interpret common fields, and how security analysts use header information during investigations. It includes definitions, analysis techniques, an example header walk-through, and an ASCII routing diagram.

---

## Purpose of Email Header Analysis

Email headers provide metadata that shows how a message was transmitted from the sender to the recipient. Security analysts review headers to:

- Identify possible spoofing attempts  
- Validate sender authenticity  
- Trace message routing across servers  
- Inspect Received chains for anomalies  
- Examine authentication results (SPF, DKIM, DMARC)  
- Determine the true originating IP address  
- Troubleshoot delivery issues  

Proper header analysis is a core skill for SOC analysts and incident responders.

---

## Common Email Header Fields

Below is a reference table for common header fields and their purpose.

| Header Field      | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| Return-Path       | Address used for bounce messages if delivery fails.                         |
| Delivered-To      | The actual mailbox that received the email.                                 |
| Received          | Shows each mail server the message passed through (bottom is first).        |
| Message-ID        | Unique identifier for the email message.                                    |
| From              | The sender’s displayed email address (can be spoofed).                      |
| To                | Intended recipient of the message.                                          |
| Subject           | Subject line of the email.                                                  |
| Date              | When the message claims it was sent.                                        |
| MIME-Version      | Version of MIME used for formatting email components.                       |
| Content-Type      | Indicates whether the email contains text, HTML, attachments, etc.          |
| SPF               | Authentication check: validates sending mail server IP.                     |
| DKIM              | Digital signature verification of email integrity.                          |
| DMARC             | Policy and alignment check based on SPF and DKIM results.                   |

---

## Reading the "Received" Chain

The **Received:** fields are the most important part of a header.

- Each mail server that handles the message adds its own Received line.
- The **topmost line** is the **most recent** server.
- The **bottommost line** is the **true origin** (unless forged).

Analysts start at the **bottom** and work upward, checking for:

- Suspicious foreign IP addresses  
- Server names that do not align with the sender’s domain  
- Time discrepancies  
- Jumps across geographic regions  
- Unexpected SMTP relays  

---

## Authentication Checks (SPF, DKIM, DMARC)

### SPF  
Compares the sending IP address with the list of authorized sending servers published by the domain.

### DKIM  
Uses cryptographic signatures to verify that the email was not altered in transit.

### DMARC  
Combines SPF and DKIM results and applies domain-level alignment policies.

Analysts use these checks to determine if a message is legitimate, spoofed, or failing authentication.

---

## Example Email Header Walk-Through

Below is a simplified sample header demonstrating the core fields.

```
Return-Path: <alerts@example.com>
Delivered-To: user@company.com
Received: from mail3.example.com (203.0.113.15)
        by mx.company.com (192.0.2.10) with ESMTPS id abc123
        Tue, 18 Feb 2025 10:14:32 -0800
Received: from app42.internal (172.16.5.22)
        by mail3.example.com (203.0.113.15)
        Tue, 18 Feb 2025 10:14:25 -0800
From: "Example Alerts" <alerts@example.com>
To: user@company.com
Subject: Security Notification
Date: Tue, 18 Feb 2025 10:14:21 -0800
Message-ID: <msgid123456@example.com>
SPF: pass
DKIM: pass
DMARC: pass
```

### Analysis Summary

- Originating host appears to be an internal app server: `172.16.5.22`
- First public-facing relay: `203.0.113.15`
- Receiving company mail server: `192.0.2.10`
- All authentication checks (SPF, DKIM, DMARC) passed.
- Header is consistent with a legitimate internal alerting system.

---

## ASCII Routing Diagram

```
+-------------------+        +-----------------------+        +---------------------+
|  Internal Host     | --->   | Sender Mail Server    | --->   | Recipient Mail Server |
| 172.16.5.22        |        | 203.0.113.15          |        | 192.0.2.10            |
+-------------------+        +-----------------------+        +---------------------+
          |                              |                               |
          +----------- SMTP ------------>+----------- SMTP --------------+
```

This diagram represents the simplified flow of the example email.

---

## Summary

Email header analysis is a foundational skill for analysts working in SOC and investigative roles. By reviewing Received chains, authentication results, and metadata fields, analysts can determine the legitimacy of a message, detect spoofing, and troubleshoot mail delivery issues. This document provides a structured approach for interpreting email headers in a security context.
