# Day 01 - Overview of Network communication and OSI model 

**Date:** April 04,2026
**Topic:** OSI Model - 7 layers and what each layer do

## What I Studied
- Computer Networking - A top down approach(Book)
- Professor messor(Youtube) - Network+ playlist - OSI model video

## What i learned 
- OSI Model (7 Layers)
- Physical Layer – Transmits raw bits through physical medium
- Data Link Layer – Ensures error-free data transfer using MAC addresses(Switching layer)
- Network Layer – Handles routing using IP addresses(Routing Layer)
- Transport Layer – Provides reliable data delivery (TCP/UDP)
- Session Layer – Manages connections between systems
- Presentation Layer – Translates, encrypts, and compresses data
- Application Layer – Provides services to end users (HTTP, FTP, etc.)

---

# Day 02 - TCP/IP Protocol Suite & How Internet Works

**Date:** April 05, 2026  
**Topic:** TCP/IP Model, Data Flow, Internet Working  

---

## From where I studied 
- TCP/IP - Gate smashers(Cybersecurity and Ethical Hacking Playlist)
- How internet works - ApnaCollege video

## What I Studied

- TCP/IP Protocol Suite (4 Layer Model)
- Why TCP/IP is used instead of OSI
- Real-life example mapping all 4 TCP/IP layers
- How the Internet works
- How data flows across the network

---

## What I Learned

### TCP/IP Model (4 Layers)

- **Application Layer** – Provides services like HTTP, HTTPS, DNS
- **Transport Layer** – Handles communication using TCP/UDP (reliability, ports)
- **Internet Layer** – Handles IP addressing and routing
- **Network Access Layer** – Handles physical transmission (MAC, cables, WiFi)

---

### Why We Use TCP/IP Instead of OSI

- TCP/IP is **practical and implemented** in real networks
- OSI is mainly a **theoretical reference model**
- TCP/IP is **simpler (4 layers vs 7 layers)**
- It was **already working (ARPANET)** before OSI was finalized
- All modern communication (Internet) is based on TCP/IP

---

### Real-Life Example (Opening www.google.com)

#### Application Layer
- Browser sends HTTP/HTTPS request to Google

#### Transport Layer
- TCP establishes connection (3-way handshake)
- Ensures reliable data transfer

#### Internet Layer
- IP address is used to route packets to Google server

#### Network Access Layer
- Data is transmitted via WiFi/Ethernet using MAC address

---

### How Internet Works

- Internet is a **network of networks**
- Devices connect through **ISP (Internet Service Provider)**
- Communication happens using **IP addresses**
- DNS converts domain names → IP addresses
- Routers forward data across multiple networks

---

### How Data Flows

1. User enters URL (e.g., www.google.com)
2. DNS resolves domain → IP address
3. TCP connection is established
4. Request is broken into **packets**
5. Packets travel through multiple routers
6. Server receives and processes request
7. Response is sent back in packets
8. Browser reassembles and displays data


## Day 02 Lab-1 - Wireshark Lab (Packet Analysis)

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
---


# Day 03 - Revision + Reading book 
## what i read
- computer networking - A top down approach is one of the best fundamentals books you can read when starting your cybersecurity or metworking journey
- It starts with what is internet and how it works
- what are the components in the connection of a device
- how internet works, what are different types of cables

-----


# Day 04 - TCP 3-Way Handshake

The TCP 3-way handshake is a process used to establish a **reliable connection** between a client and a server.

## Key Points
- TCP is **connection-oriented** and ensures reliable data transfer.
- Synchronizes **sequence numbers (ISN)** for tracking data.
- Negotiates parameters like **MSS** and **window size** before communication.

## Steps
1. **SYN** – Client initiates connection  
2. **SYN + ACK** – Server acknowledges and responds  
3. **ACK** – Client confirms → connection established  

## Common TCP Flags
- **SYN** → Start connection  
- **ACK** → Acknowledge  
- **FIN** → Close connection  
- **RST** → Abort connection  

Ensures ordered, reliable, and error-checked communication.

-----


# Day 05 Lab-2 - Accessing wireshark using CLI(Dumpcap)
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

## Day 6 Lab-3 – Wireshark Basics

### Where to Place Wireshark
Used to troubleshoot **application connectivity issues** across a network.

**Approach:**
- Capture traffic between key points:
  - Access Point ↔ Switch  
  - Switch ↔ Internet  
  - Internet ↔ Other Switches  
- If possible, **mirror/divert traffic** to analyze centrally  
- If not:
  - Install Wireshark on **client side** (user POV)
  - For repeated issues → capture on **server side**

---

### Wireshark Filtering

#### 1. Capture Filters (Pre-filtering)
- Applied **before capturing**
- Filters traffic at source → reduces load

#### 2. Display Filters (Post-filtering)
- Applied **after capture**
- Helps analyze specific packets

---

### 🧪 Common Filters
- Protocols: `arp`, `dns`, `ip`, `tcp`, `udp`
- IP filtering:  
  - `ip.addr == x.x.x.x`  
  - `ip.addr == x.x.x.x and/or ip.addr == x.x.x.x`
- Port filtering:  
  - `tcp.port == 80`  
  - `tcp.port == 443`
- Exclude traffic:  
  - `not arp` / `not tcp` / `not ip`
- Content filtering:  
  - `frame contains "google"` (case-sensitive)  
  - `frame matches "google"` (case-insensitive)

---
