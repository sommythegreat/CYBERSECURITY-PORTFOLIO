## Lab 05: Detecting Port Scanning Activity

### Objective
Detect and analyze port scanning activity using Wireshark. Identify the characteristics of a SYN scan and document the evidence.

### Scenario
Unusual traffic was observed on the system. After investigation, multiple SYN packets were found targeting different ports in a short time, indicating a port scan.

### Tools Used
- Kali Linux
- Wireshark
- Nmap

### Methodology
1. Started a packet capture in Wireshark
2. Performed a SYN scan using: (nmap -sS 127.0.0.1)
3. Stopped the capture after the scan completed
4. Applied the filter: (tcp.flags.syn == 1 and tcp.flags.ack == 0)
5. Analysed the resulting traffic 

### Findings
•  A large number of TCP SYN packets were observed
•  All packets originated from the same source IP
•  Destination ports varied (eg, 22, 80, 443, 8080, etc.)
•  Most connections did not complete the 3-way handshake
•  This behavior is consistent with a SYN scan

### Key Indicators of Port Scanning
•  Multiple SYN packets in a short time
•  Different destination ports
•  Lack of full TCP handshake
•  Same source IP repeatedly probing the host

### Conclusion
   The captured traffic clearly shows port scanning activity. Using Wireshark display filters made it easy to isolate and confirm the suspicious behavior.

Screenshots
•  Nmap terminal command
<img width="3840" height="2160" alt="NMAP TERMINAL COMMAND" src="https://github.com/user-attachments/assets/937260a7-9310-4833-b052-1e3d4720003d" />

•  Full packet capture
<img width="3840" height="2160" alt="FULL PACKET CAPTURE" src="https://github.com/user-attachments/assets/3872c056-6d04-4dc2-939b-0cb1a12a2c6f" />

•  Filtered SYN packets
<img width="3840" height="2160" alt="FILTERED VIEW" src="https://github.com/user-attachments/assets/40d3d969-174b-418b-98b5-38a4fc1377b1" />

•  Detailed SYN packet
<img width="3840" height="2160" alt="A SINGLE DETAILED SYN PACKET" src="https://github.com/user-attachments/assets/464233f4-4f08-4acb-b309-6c570e02df65" />

