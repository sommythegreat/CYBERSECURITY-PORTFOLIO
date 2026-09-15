
# Cybersecurity Portfolio

Hands-on networking and cybersecurity labs documenting my learning journey after completing the Google Cybersecurity Professional Certificate and Cisco Introduction to Cybersecurity.

## Cisco Packet Tracer Labs

### Lab 01: Basic LAN Connectivity with Cisco Packet Tracer

- Built a simple local area network with 2 PCs, 1 Switch, and 1 Router
- Configured static IP addressing and verified connectivity using ping
- [View Full Lab](https://github.com/sommythegreat/CYBERSECURITY-PORTFOLIO/blob/main/labs/Cisco-Packet-Tracer/Lab-01-Basic-LAN-Connectivity.md)

### Lab 02: Connecting Two Networks Using a Router

- Created two separate networks and connected them using a Router
- Configured Router interfaces using CLI
- Understood Default Gateway and inter-network communication
- [View Full Lab](https://github.com/sommythegreat/CYBERSECURITY-PORTFOLIO/blob/main/labs/Cisco-Packet-Tracer/Lab-02-Connecting-Two-Networks.md)

### Lab 03: DHCP vs Static IP Configuration

- Configured both Static IP and DHCP on the same network
- Set up a Router as a DHCP server using CLI
- Verified connectivity between Static and DHCP clients
- [View Full Lab](https://github.com/sommythegreat/CYBERSECURITY-PORTFOLIO/blob/main/labs/Cisco-Packet-Tracer/Lab-03-DHCP-vs-Static-IP.md)

### Lab 04: VLAN Segmentation with Router-on-a-Stick

- Segmented Admin and Staff departments on a single switch using VLANs (VLAN 10 & VLAN 20)
- Configured router subinterfaces with 802.1Q encapsulation for inter-VLAN routing
- Combined static IP addressing (Admin) with DHCP (Staff) across separate VLANs
- Troubleshot and resolved DHCP failures caused by incorrect VLAN port assignment
- [View Full Lab](https://github.com/sommythegreat/CYBERSECURITY-PORTFOLIO/blob/main/labs/Cisco-Packet-Tracer/Lab-04-Department-Network-With-Vlan-Router-On-A-Stick.md)

## Wireshark Labs

### Lab 01: Packet Capture and Traffic Analysis with Wireshark

- Captured live network traffic (8545 packets) using Wireshark in Kali Linux
- Analyzed packet structure across OSI layers (Frame, Linux cooked capture, IPv4, ICMP)
- Identified multiple protocols in a single capture: ICMP (ping), TCP, DNS
- Understood packet anatomy: source/destination IPs, TTL, protocol types, hex dump representation
- [View Full Lab](https://github.com/sommythegreat/CYBERSECURITY-PORTFOLIO/blob/main/labs/Wireshark/Lab-01-Packet-Capture-and-Traffic-Analysis.md)

### Lab 02: TCP 3-Way Handshake and Protocol Dissection
- Captured and analyzed a complete TCP 3-way handshake
- Used Follow TCP Stream to reconstruct an HTTP conversation
- Understood how reliable connections are established
- [View Full Lab](labs/Wireshark/Lab-02-TCP-3-Way-Handshake-and-Protocol-Dissection.md)

### Lab 03: Application-Layer Protocol Analysis

- Analyzed HTTP GET requests and server responses in plaintext from neverssl.com
- Examined DNS queries showing domain-to-IP resolution on port 53 (UDP)
- Compared HTTP (port 80, plaintext) vs. HTTPS (port 443, encrypted)
- Understood why encryption matters: plaintext exposes headers, data, user-agent
- Identified protocol differences: DNS (UDP) vs. HTTP/HTTPS (TCP)
- [View Full Lab](https://github.com/sommythegreat/CYBERSECURITY-PORTFOLIO/blob/main/labs/Wireshark/Lab-03-Application-Layer-Protocol-Analysis.md)


## Skills Demonstrated

- IP Addressing & Subnetting
- Network Topology Design
- Static Routing Concepts
- Router Configuration (CLI)
- DHCP Configuration (CLI)
- VLAN Configuration (CLI)
- Router-on-a-Stick (Inter-VLAN Routing)
- Access Control Lists (ACLs)
- Packet Capture & Analysis
- Protocol Filtering (DNS, TCP, TLS, HTTPS)
- Port Analysis & Identification
- TCP Stream Analysis
- Encrypted vs. Plaintext Traffic Recognition
- Protocol Identification (TCP, UDP, DNS, HTTP/HTTPS, ICMP, TLSv1.3)
- OSI Layer Analysis
- Network Troubleshooting
- Technical Documentation


## Certifications

- Google Cybersecurity Professional Certificate
- APTlearn.io Cybersecurity Certificate
- Cisco Introduction to Cybersecurity
