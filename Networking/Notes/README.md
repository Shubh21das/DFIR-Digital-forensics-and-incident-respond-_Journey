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
