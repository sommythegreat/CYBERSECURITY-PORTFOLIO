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
•  Destination ports varied (e.g. 22, 80, 443, 8080, etc.)
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
•  Full packet capture
•  Filtered SYN packets
•  Detailed SYN packet
