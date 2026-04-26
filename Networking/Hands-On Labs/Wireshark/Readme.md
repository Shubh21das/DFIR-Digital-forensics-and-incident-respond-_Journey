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

# Day 05 - Accessing wireshark using CLI(Dumpcap)
## What is Dumpcap ?
- Dumpcap is a tool of wireshark that can be accessed through CLI(cmd).
- it has all the features of wireshark.

## Why dumpcap and not wireshark ?
- Everytime GUI(Wireshark) will not be available and therefore using dumpcap makes it easier and more accessible

## how to use dumpcap ?
- Step 01 - add the wireshark directory to PATH.
- Step 02 - open CMD and type dumpcap
- Step 03 - it will start capturing the packets and save it in a temp file inside wireshark directory

## dumpcap commands 
1. Dumpcap -h - Lists the commands of dumpcap
2. dumpcap -w - Write the captured packets into the .pcap or .pcapng file
3. dumpcap -i - lists the interfaces available
4. dumpcap -b - initiates Ring Buffer

## key learning 
- Using dumpcap(CLI) instead of wireshark to capture packets
- learned how to capture, store and view .pcap or .pcapng files
- learned using Ring buffer to limit the capture size, path and buffer(in MB)

---

