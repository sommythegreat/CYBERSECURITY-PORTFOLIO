## Lab 02: Connecting Two Networks Using a Router

### Objective
Create two separate networks, connect them using a router, configure IP addressing and default gateways, and verify communication between devices on different networks.

### Topology
- Network 1: PC0 and PC2 connected to Switch0 → Router
- Network 2: PC1 and PC3 connected to Switch1 → Router
- Router connects both networks

### IP Addressing Scheme

| Device  | Interface            | IP Address    | Subnet Mask     | Default Gateway |
|---------|----------------------|---------------|-----------------|-----------------|
| PC0     | FastEthernet0        | 192.168.1.10  | 255.255.255.0   | 192.168.1.1     |
| PC2     | FastEthernet0        | 192.168.1.15  | 255.255.255.0   | 192.168.1.1     |
| Router  | GigabitEthernet0/0   | 192.168.1.1   | 255.255.255.0   | -               |
| Router  | GigabitEthernet0/1   | 192.168.2.1   | 255.255.255.0   | -               |
| PC1     | FastEthernet0        | 192.168.2.10  | 255.255.255.0   | 192.168.2.1     |
| PC3     | FastEthernet0        | 192.168.2.15  | 255.255.255.0   | 192.168.2.1     |

### Steps Performed
1. Created two separate networks using switches
2. Connected both switches to the Router
3. Configured static IP addresses and default gateways on all PCs
4. Configured both router interfaces using CLI
5. Verified connectivity with successful pings across both networks

### Key Concepts Learned
- Difference between devices on the same network vs different networks
- Role of the Default Gateway
- Why a Router needs its own IP address on each network it connects to
- Basic Router CLI configuration (`interface`, `ip address`, `no shutdown`)

### Troubleshooting Notes
- Experienced IP address conflicts on the Router
- Fixed incorrect gateway configurations
- Learned the importance of unique IP addresses on every device

### Verification
Successful pings between devices on Network 1 and Network 2 (0% packet loss in both directions).

### Screenshots
- Full Network Topology
<img width="1600" height="856" alt="NETWORK TOPOLOGY (USING ROUTER TO CONNECT DIFFERENT NETWORK)" src="https://github.com/user-attachments/assets/89b222d4-6bef-4020-9288-ce3241d936b3" />

- Router CLI Configuration
<img width="1598" height="857" alt="ROUTER CLI CONFIGURATION" src="https://github.com/user-attachments/assets/ca9a7767-163e-4add-8a19-b937c908bb8e" />

- Successful Cross-Network Ping
<img width="1600" height="863" alt="SUCCESSFUL PING FROM PC0 TO PC2, PC1, AND PC3" src="https://github.com/user-attachments/assets/776b09c2-0f58-4a9d-be22-f5def2aa2299" />
<img width="1600" height="860" alt="SUCCESSFUL PING FROM PC2 TO PC0, PC1, AND PC3" src="https://github.com/user-attachments/assets/cca0cc0a-3152-4520-830a-e6f2e4b0f8bb" />
<img width="1600" height="859" alt="SUCCESSFUL PING FROM PC3 TO PC1, PC0, AND PC2" src="https://github.com/user-attachments/assets/c94cdf4b-be3b-46b4-8713-4a20199cfb36" />
<img width="1600" height="854" alt="SUCCESSFUL PING FROM PC1 TO PC3, PC0, AND PC2" src="https://github.com/user-attachments/assets/bace6ccb-0a4f-402a-93bc-9de9c7f9fed2" />
