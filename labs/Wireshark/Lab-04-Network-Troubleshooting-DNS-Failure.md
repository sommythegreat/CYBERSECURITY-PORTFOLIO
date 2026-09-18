## Lab 04: Network Troubleshooting – DNS Failure Analysis

### Objective
Simulate and troubleshoot a real-world network issue where a user cannot resolve domain names. Capture the traffic, identify the root cause using Wireshark, and confirm the fix.

### Scenario
A user reported that they could no longer access websites (e.g. `example.com`), receiving the error:

### Temporary failure in name resolution
Other basic connectivity appeared normal. The task was to investigate the issue using packet analysis.

### Tools Used
- Kali Linux (Virtual Machine)
- Wireshark
- Terminal (`ping`, `resolv.conf`)

### Methodology
1. Started a packet capture in Wireshark
2. Verified normal connectivity by successfully pinging `example.com`
3. Simulated a DNS failure by pointing the system DNS to `127.0.0.1`
4. Attempted to ping `example.com` again (failed as expected)
5. Analyzed the capture using the `dns` filter
6. Identified the root cause
7. Restored the correct DNS settings and verified connectivity

### Findings

**Before the issue:**
- DNS queries were sent to `192.168.0.1`
- Valid DNS responses were received

**During the issue:**
- DNS queries were being sent to `127.0.0.1`
- The response was: `ICMP Destination unreachable (Port unreachable)`
- No valid DNS resolution occurred

### Root Cause
The system’s DNS configuration was changed to `127.0.0.1` (localhost).  
Since no DNS service was running on the local machine, all name resolution attempts failed.

### Resolution
The DNS configuration was restored to a valid nameserver (`192.168.0.1`).  
Connectivity was successfully restored and verified with a working ping.

### Key Lessons
- DNS failures often present as “website not loading” or “name resolution” errors
- Wireshark can clearly show where DNS queries are being sent
- ICMP “Port unreachable” is a strong indicator that the target service is not available
- Always verify DNS configuration when troubleshooting connectivity issues

### Screenshots
- Terminal showing failed and successful pings
<img width="3840" height="2160" alt="TERMINAL PING COMMAND 1" src="https://github.com/user-attachments/assets/d9895508-17fc-4f01-adf0-f2a805766efd" />
<img width="3840" height="2160" alt="TERMINAL PING COMMAND 2" src="https://github.com/user-attachments/assets/90172cf5-56a0-4dfc-bd2f-b941a6c40ae9" />

- Full packet capture
<img width="3840" height="2160" alt="FULL PACKET CAPTURED" src="https://github.com/user-attachments/assets/d35cd10b-2508-4e1c-903c-35a3a59e8612" />

- DNS filter results showing queries to `127.0.0.1`
<img width="3840" height="2160" alt="DNS FILTER RESULT" src="https://github.com/user-attachments/assets/26c67ed6-c2cb-4045-a5a4-abf49cd3c1cc" />

- Detailed ICMP Port Unreachable packet
<img width="3840" height="2160" alt="DETAILED DNS   ICMP UNREACHABLE PACKET" src="https://github.com/user-attachments/assets/4fafda72-3549-4141-8fa7-8e0348f54e9d" />
