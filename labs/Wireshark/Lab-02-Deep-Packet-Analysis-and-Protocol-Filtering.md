## Lab 02: Deep Packet Analysis and Protocol Filtering

### Objective
Filter captured network traffic by protocol and port number, analyze DNS queries, and follow TCP streams to understand encrypted communication patterns.

### Tools Used
- Kali Linux (Virtual Machine)
- Wireshark 4.6.6
- Web browser for traffic generation
- ping command for DNS queries

### Methodology
1. Captured live network traffic on Kali using Wireshark
2. Filtered traffic by DNS protocol to isolate hostname lookups
3. Analyzed individual DNS packets to understand query/response structure
4. Captured HTTPS/TLS traffic and followed TCP streams
5. Examined encrypted conversation between client and Google servers

### Key Findings

**DNS Analysis:**
- DNS queries use port 53 (UDP)
- Queries travel from client (10.0.2.15) to DNS server (192.168.0.1)
- Multiple domain queries observed: google.com, api. adtrafficquality, pageads. google, etc.
- Query types include A (IPv4), AAAA (IPv6), and HTTPS records

**TCP Stream Analysis:**
- Followed HTTPS/TLS stream to google.com (1,279 KB total data)
- Conversation is encrypted — only metadata visible (source, destination, ports, volume)
- Protocol: TLSv1.3 with h2/HTTP/1.1 application layer
- Source port: 38260 (ephemeral), Destination port: 443 (HTTPS standard)
- Demonstrates why HTTPS is secure: payload is unreadable

### Ports Observed
- **Port 53** — DNS queries
- **Port 80** — HTTP traffic
- **Port 443** — HTTPS/TLS encrypted traffic

### Learning Outcomes
- Mastered traffic filtering by protocol (DNS, TCP, TLS)
- Understood port numbers and their protocols
- Learned to follow TCP streams for end-to-end communication analysis
- Recognized encrypted vs. plaintext communication patterns
- Deepened understanding of OSI layers in real network traffic

### Screenshots

- FULL PACKET CAPTURE SHOWING 8545 PACKETS WITH MULTIPLE PROTOCOLS
<img width="3840" height="2160" alt="FULL PACKET CAPTURE SHOWING 12183 PACKETS WITH MULTIPLE PROTOCOLS" src="https://github.com/user-attachments/assets/6c3c98ee-be2c-41f7-a07e-c60b179dc7f2" />

- DNS FILTERING & ANALYSIS
<img width="3840" height="2160" alt="DNS FILTERING   ANALYSIS" src="https://github.com/user-attachments/assets/61d6cebe-b1fa-4ec3-9dac-4b143b8c73b8" />

- TCP STREAM FOLLOWING & ENCRYPTED HTTPS CONVERSATION
<img width="3840" height="2160" alt="TCP STREAM FOLLOWING   ENCRYPTED HTTPS COVERSATION" src="https://github.com/user-attachments/assets/e8cf6e3b-6dc7-40ab-88f0-7ee1d727fc9b" />
