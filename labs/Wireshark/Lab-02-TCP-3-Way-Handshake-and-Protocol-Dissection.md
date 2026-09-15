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
| 1      | `[SYN]`     | Client → Server  | Client requests to start a connection|
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
  <img width="3840" height="2160" alt="FULL PACKETS CAPTURED" src="https://github.com/user-attachments/assets/8f91fe29-6fe5-437b-9b75-86b094bd7461" />

- TCP 3-Way Handshake packets (`[SYN]`, `[SYN, ACK]`, `[ACK]`)
<img width="3840" height="2160" alt="THE 3-WAY HANDSHAKE PACKETS" src="https://github.com/user-attachments/assets/dcbb3404-844c-4722-a7f9-8db8f3a89d6c" />

- Individual packet details showing TCP flags
<img width="3840" height="2160" alt="AN INDIVIDUAL PACKET DETAILS" src="https://github.com/user-attachments/assets/70cb2f0b-ad6d-432d-9d3b-b76f11eee30e" />

- Follow TCP Stream (HTTP Request & Response)
<img width="3840" height="2160" alt="FOLLOWED TCP STREAM" src="https://github.com/user-attachments/assets/1b546505-76e3-491f-891e-35e3f8830735" />
