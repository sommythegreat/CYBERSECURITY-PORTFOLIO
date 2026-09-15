## Lab 02: TCP 3-Way Handshake and Protocol Dissection

### Objective
Capture live network traffic and analyze a complete TCP 3-way handshake. Reconstruct the conversation using Follow TCP Stream and understand how a reliable connection is established between a client and a server.

### Tools Used
- Kali Linux (Virtual Machine)
- Wireshark
- Firefox browser

### Methodology
1. Started a packet capture in Wireshark
2. Visited `http://example.com` to generate HTTP traffic
3. Stopped the capture
4. Applied the filter `tcp.stream eq 3` to isolate a single conversation
5. Identified the TCP 3-way handshake packets
6. Used **Follow TCP Stream** to reconstruct the full HTTP conversation

### TCP 3-Way Handshake Analysis

The following packets formed the handshake:

| Packet | Flags       | Direction       | Purpose                              |
|--------|-------------|------------------|--------------------------------------|
| 1      | `[SYN]`     | Client → Server  | Client requests to start a connection |
| 2      | `[SYN, ACK]`| Server → Client  | Server acknowledges and agrees       |
| 3      | `[ACK]`     | Client → Server  | Client confirms the connection       |

After the handshake was completed, the client sent an HTTP GET request and the server responded with `HTTP/1.1 200 OK`.

### Key Findings
- Successfully identified a clean TCP 3-way handshake
- Observed the transition from connection establishment to actual data transfer (HTTP)
- Used Follow TCP Stream to view the readable application-layer data
- Confirmed that SYN, SYN-ACK, and ACK packets are separate and sequential

### Learning Outcomes
- Understood how TCP establishes a reliable connection
- Learned how to isolate a single conversation using `tcp.stream`
- Practiced protocol dissection across Transport and Application layers
- Gained experience reconstructing conversations in Wireshark

### Screenshots
- Full packet capture
- TCP 3-Way Handshake packets (`[SYN]`, `[SYN, ACK]`, `[ACK]`)
- Individual packet details showing TCP flags
- Follow TCP Stream (HTTP Request & Response)