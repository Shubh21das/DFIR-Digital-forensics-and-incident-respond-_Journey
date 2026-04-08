## Day 02 - Wireshark Lab (Packet Analysis)

### Objective
- Capture and analyze network packets using Wireshark  
- Understand how TCP/IP layers appear in real traffic  

---

### Tool Used
- Wireshark (Packet Analyzer)

---

### What I Observed

- Captured live HTTPS traffic (TCP + TLSv1.3)
- Observed packet details like:
  - Source & Destination IP
  - Port numbers (443 - HTTPS)
  - Sequence & Acknowledgment numbers
- Identified retransmissions and out-of-order packets

---

### TCP/IP Layer Mapping (from Capture)

| Wireshark Field | TCP/IP Layer |
|----------------|-------------|
| Frame          | Not a layer (capture metadata) |
| Ethernet II    | Network Access Layer |
| IPv6           | Internet Layer |
| TCP            | Transport Layer |

---

### Basic Uses of Wireshark

- Network troubleshooting  
- Packet-level analysis  
- Detecting anomalies (retransmissions, packet loss)  
- Security monitoring (suspicious traffic)  

---

### Key Learning

- Real network communication follows TCP/IP layers  
- Data is transmitted in packets, not as a whole  
- Wireshark helps visualize actual packet flow  

---
