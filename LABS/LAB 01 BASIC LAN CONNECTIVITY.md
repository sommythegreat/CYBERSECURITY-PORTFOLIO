### Hands-on networking and cybersecurity labs with Cisco Packet Tracer

---

## Lab 01: Basic LAN Connectivity with Cisco Packet Tracer

### Objective
Build a simple local area network with 2 PCs, 1 Switch, and 1 Router. Configure IP addressing and verify connectivity using ping.

### Topology
- PC0 connected to Switch0
- PC1 connected to Switch0
- Switch0 connected to Router0 (GigabitEthernet0/0)
- <img width="1600" height="854" alt="MY NETWORK TOPOLOGY" src="https://github.com/user-attachments/assets/9ec3de9d-cfeb-4f4a-9001-4d0ef03a4622" />


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
<img width="1600" height="854" alt="PC1 IP CONFIGURATION" src="https://github.com/user-attachments/assets/4b54084c-2095-453e-9226-19cda45a27ad" />
5. Configured IP address on Router interface and enabled the port (Port Status = On)
<img width="1600" height="860" alt="ROUTER PORT NOT YET ON" src="https://github.com/user-attachments/assets/71690eae-c3f6-42b7-a646-45de70ebb457" />
<img width="1600" height="857" alt="ROUTER PORT ON" src="https://github.com/user-attachments/assets/a214bb71-e006-40b5-967d-5770c69090fc" />
<img width="1600" height="857" alt="ROUTER PORT ON SUCCESSFULL" src="https://github.com/user-attachments/assets/c84c3d80-9b0d-430d-8d0d-80fd16dfc999" />
6. Verified connectivity using the `ping` command

### Troubleshooting Notes
- Initially connected PC1 to the Switch Console port (Console is for management only, not data traffic) by mistake, which made my first ping from PC1 to PC0 unsuccessful
- <img width="1600" height="863" alt="UNSUCCESSFUL PING TO PC0 BEFORE RECONNECTNG PC1 TO THE RIGHT SWITCH PORT" src="https://github.com/user-attachments/assets/0193e773-db83-447c-b2d2-d7accea47235" />

- Corrected by reconnecting PC1 to the right Switch port (fastEthernet0/3)
- <img width="1589" height="866" alt="AFTER RECONNECTING PC1 CORRECTLY TO THE RIGHT SWITCH PORT" src="https://github.com/user-attachments/assets/5ac50d46-7f78-402c-837a-64b6a908e26c" />
- Learned the difference between Console port and network interfaces

### Verification
Successful ping from PC1 to PC0:
- 4 packets sent, 4 received, 0% loss
- <img width="1600" height="900" alt="SUCCESSFUL PING TO PC0 FROM PC1 AFTER RECONNECTNG PC1 TO THE RIGHT SWITCH PORT" src="https://github.com/user-attachments/assets/fe994e8f-e247-4671-b139-2fd084a48ea0" />


### Skills Demonstrated
- Basic network topology design
- IP addressing and subnetting
- Device configuration in Cisco Packet Tracer
- Systematic troubleshooting of connectivity issues
