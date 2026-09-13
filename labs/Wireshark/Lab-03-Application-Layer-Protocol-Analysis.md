## Lab 03: Application-Layer Protocol Analysis

### Objective
Analyze HTTP request/response headers, DNS queries and responses, and understand how application-layer protocols communicate over the network at readable (plaintext) level.

### Tools Used
- Kali Linux (Virtual Machine)
- Wireshark 4.6.6
- Firefox browser
- neverssl.com (intentionally unencrypted HTTP site)

### Methodology
1. Captured live network traffic on Kali using Wireshark
2. Browsed to neverssl.com to generate HTTP traffic (plaintext, not HTTPS)
3. Analyzed DNS queries showing domain-to-IP resolution
4. Examined HTTP GET request and server response headers
5. Reviewed HTML payload delivered by server
6. Compared plaintext vs. encrypted communication

### Key Findings

**DNS Query Analysis:**
- Protocol: UDP (fast, connectionless)
- Port: 53 (DNS standard port)
- Query: "What's the IP for neverssl.com?"
- Source: Client machine (10.0.2.15)
- Destination: DNS server (192.168.0.1)
- Frame size: 103 bytes
- Query type: Standard DNS lookup

**HTTP Request/Response (Plaintext):**
- **Request Method:** GET / HTTP/1.1
- **Host Requested:** neverssl.com
- **User-Agent:** Mozilla/5.0 (Firefox on Linux)
- **Server Response:** HTTP/1.1 200 OK
- **Server Software:** Apache/2.4.68
- **Content Type:** text/html
- **Content Length:** 1900 bytes
- **Entire HTML body visible** in plaintext: `<html>`, `<head>`, `<title>`, CSS styling, etc.

**Protocol Comparison:**
- **DNS:** Port 53, UDP, hostname → IP resolution
- **HTTP:** Port 80, TCP, request/response in plaintext
- **HTTPS:** Port 443, TCP wrapped in TLS encryption (payload unreadable)

### Critical Insight: Plaintext vs. Encrypted

**HTTP (Plaintext):**
- Entire request visible: headers, host, user-agent
- Entire response visible: HTML, CSS, data
- Anyone on the network can read what's being requested and sent
- **Security risk:** Passwords, personal data exposed

**HTTPS (Encrypted):**
- Only metadata visible: IPs, ports, data size
- Payload (actual request/response) encrypted
- Only client and server can read content
- **Security benefit:** Data protected from network eavesdropping

### Ports Observed
- **Port 53** — DNS query/response
- **Port 80** — HTTP unencrypted web traffic

### Learning Outcomes
- Understood HTTP GET requests and server responses
- Saw plaintext data transmission (why HTTPS matters)
- Learned DNS resolution at packet level
- Compared UDP (DNS) vs. TCP (HTTP) protocols
- Recognized the importance of encryption for sensitive data
- Deepened understanding of application-layer protocols

### Screenshots
- FULL PACKETS CAPTURED
<img width="3840" height="2160" alt=" FULL PACKET CAPTURE SHOWING 3191 PACKETS WITH MULTIPLE PROTOCOLS" src="https://github.com/user-attachments/assets/b321d5ba-34f6-4db0-bbf5-2af4f1b32a6d" />

- HTTP STREAM
<img width="3840" height="2160" alt="FOLLOWED HTTP SREAM" src="https://github.com/user-attachments/assets/e67e0dfe-0414-4668-9f69-aad966bb8d35" />

- DNS PACKET
<img width="3840" height="2160" alt="DNS PACKET DETAILS" src="https://github.com/user-attachments/assets/eccea78c-b60a-4740-8695-fbf5f116a5b2" />
