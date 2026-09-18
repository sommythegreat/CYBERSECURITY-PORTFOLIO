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
- Full packet capture
- DNS filter results showing queries to `127.0.0.1`
- Detailed ICMP Port Unreachable packet