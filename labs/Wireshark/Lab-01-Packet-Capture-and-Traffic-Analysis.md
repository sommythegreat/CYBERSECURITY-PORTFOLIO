### Objective
Capture live network traffic using Wireshark and analyze packet structure to understand how data moves across networks at different OSI layers.

### Tools Used
- Kali Linux (Virtual Machine)
- Wireshark 4.6.6
- ping command for traffic generation

### Methodology
1. Opened Wireshark on Kali Linux
2. Selected the network interface and started packet capture
3. Generated ICMP traffic by pinging google.com from the terminal
4. Captured 8545 packets over ~1 minute
5. Analyzed individual packets to understand OSI layers

### Key Findings
The capture revealed multiple protocol types:
- **ICMP** — Internet Control Message Protocol (ping requests and replies)
- **TCP** — Transmission Control Protocol (connection-based traffic)
- **DNS** — Domain Name System (hostname resolution)

### Packet Analysis
When examining an individual ICMP packet (Frame 8538):
- **Frame Layer** — Shows complete packet size: 100 bytes on the wire
- **Linux Cooked Capture Layer** — Interface metadata
- **Internet Protocol Layer** — IPv4 packet with Source IP: 10.0.2.15, Destination IP: 216.58.204.174
- **Internet Control Message Protocol Layer** — ICMP echo request/reply for ping operation
- **Hex Dump** — Raw bytes showing the packet's binary representation

### Learning Outcomes
- Successfully captured and analyzed real network traffic
- Identified different protocols in a live capture
- Understood packet structure across multiple OSI layers
- Learned to interpret Wireshark's detailed packet breakdown

### Screenshots
- Full packet capture showing 8545 packets with multiple protocols
<img width="3840" height="2160" alt="FULL PACKET CAPTURE SHOWING 8545 PACKETS WITH MULTIPLE PROTOCOLS" src="https://github.com/user-attachments/assets/b40db70c-3381-4d9e-9f5c-26a322bdbfa0" />

- Detailed breakdown of an individual ICMP packet showing all layers
<img width="3837" height="2010" alt="DETAILED BREAKDOWN OF AN INDIVIDUAL ICMP PACKET SHOWING ALL LAYERS" src="https://github.com/user-attachments/assets/f90feb70-8c23-4662-96cc-9d6459a40339" />
