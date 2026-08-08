### Hands-on networking and cybersecurity labs with Cisco Packet Tracer

---

## Lab 01: Basic LAN Connectivity with Cisco Packet Tracer

### Objective
Build a simple local area network with 2 PCs, 1 Switch, and 1 Router. Configure IP addressing and verify connectivity using ping.

### Topology
- PC0 connected to Switch0
- PC1 connected to Switch0
- Switch0 connected to Router0 (GigabitEthernet0/0)

### IP Addressing Scheme

| Device   | Interface            | IP Address     | Subnet Mask     | Default Gateway |
|----------|----------------------|----------------|-----------------|-----------------|
| PC0      | FastEthernet0        | 192.168.1.10   | 255.255.255.0   | 192.168.1.1     |
| PC1      | FastEthernet0        | 192.168.1.15   | 255.255.255.0   | 192.168.1.1     |
| Router0  | GigabitEthernet0/0   | 192.168.1.1    | 255.255.255.0   | -               |

### Steps Performed
1. Added devices (2 × PC-PT, 1 × 2960 Switch, 1 × 1941 Router)
2. Connected devices using Copper Straight-Through cables
3. Configured static IP addresses on both PCs
4. Configured IP address on Router interface and enabled the port (Port Status = On)
5. Verified connectivity using the `ping` command

### Troubleshooting Notes
- Initially connected PC1 to the Router’s Console port by mistake (Console is for management only, not data traffic)
- Corrected by reconnecting PC1 to the Switch
- Learned the difference between Console port and network interfaces

### Verification
Successful ping from PC1 to PC0:
- 4 packets sent, 4 received, 0% loss

### Skills Demonstrated
- Basic network topology design
- IP addressing and subnetting
- Device configuration in Cisco Packet Tracer
- Systematic troubleshooting of connectivity issues
