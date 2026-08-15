## Lab-03-DHCP-vs-Static-IP Configuration

### Objective
Create a network that demonstrates both Static IP and DHCP configuration. Configure some PCs with static IP addresses and others to obtain IP addresses automatically from a DHCP server running on the Router.

### Topology
- 1 × 1941 Router
- 1 × 2960 Switch
- 4 × PCs (PC0, PC1, PC2, PC3)
- All PCs connected to the Switch
- Switch connected to the Router

### IP Addressing Scheme

| Device  | Interface            | IP Address     | Subnet Mask     | Default Gateway | Method  |
|---------|----------------------|----------------|-----------------|-----------------|---------|
| PC0     | FastEthernet0        | 192.168.1.10   | 255.255.255.0   | 192.168.1.1     | Static  |
| PC1     | FastEthernet0        | 192.168.1.15   | 255.255.255.0   | 192.168.1.1     | Static  |
| Router  | GigabitEthernet0/0   | 192.168.1.1    | 255.255.255.0   | -               | Static  |
| PC2     | FastEthernet0        | 192.168.1.2    | 255.255.255.0   | 192.168.1.1     | DHCP    |
| PC3     | FastEthernet0        | 192.168.1.3    | 255.255.255.0   | 192.168.1.1     | DHCP    |

### Steps Performed
1. Built the topology (Router + Switch + 4 PCs)
2. Configured Static IP addresses on PC0 and PC1
3. Configured the Router using CLI
4. Configured a  DHCP pool on the Router using CLI
5. Set PC2 and PC3 to obtain IP addresses automatically (DHCP)
6. Verified connectivity with successful pings between all devices

### Key Concepts Learned
- Difference between Static IP and DHCP
- How a Router can act as a DHCP server
- Importance of correct Default Gateway
- Basic DHCP configuration using Cisco CLI

### Troubleshooting Notes
- Initially received APIPA addresses (169.254.x.x) because the Router interface was not properly configured
- Fixed by assigning IP 192.168.1.1 to the Router interface and enabling it with `no shutdown.`
- Encountered a DHCP address conflict warning (normal when the gateway IP is within the pool)

### Verification
- Static PCs (PC0 & PC1) communicated successfully
- DHCP PCs (PC2 & PC3) received valid IP addresses from the Router
- All devices could ping each other with 0% packet loss

### Screenshots
- Full Network Topology
<img width="1600" height="858" alt="NETWORK TOPOLOGY" src="https://github.com/user-attachments/assets/85b824a1-52d7-4135-8d12-05439fd106e3" />

- Static IP Configuration (PC0)
<img width="1600" height="861" alt="STATIC IP CONFIGURATION ON PC0" src="https://github.com/user-attachments/assets/2461c1d4-f7ad-4de7-81cc-e539612e18a2" />

- DHCP CLI Configuration on Router
<img width="1600" height="854" alt="DHCP IP CLI CONFIGURATION" src="https://github.com/user-attachments/assets/b8e54333-b582-4617-9e3c-324ddaaf4346" />

- Router CLI IP configuration
<img width="1600" height="854" alt="ROUTER IP CLI CONFIGURATION" src="https://github.com/user-attachments/assets/fe9d19a2-fb87-4212-897d-c2d727a86cfd" />

- Automatic DHCP IP Configuration on PC2
<img width="1600" height="854" alt="AUTOMATIC DHCP IP CONFIGURATION ON PC2" src="https://github.com/user-attachments/assets/73a13269-ac95-43b4-b093-df4051e6a755" />


- Successful Ping Results
<img width="1600" height="852" alt="SUCCESSFUL PING FROM PC2 TO PC3, PC1,   PC0" src="https://github.com/user-attachments/assets/27121c5d-a1cd-489a-9c78-a09484420c7b" />
<img width="1600" height="855" alt="SUCCESSFUL PING FROM PC3 TO PC2, PC1,   PC0" src="https://github.com/user-attachments/assets/705a8398-172b-4722-85b6-08324a68fe14" />
<img width="1600" height="859" alt="SUCCESSFUL PING FROM PC0 TO PC2, PC1,   PC3" src="https://github.com/user-attachments/assets/46f723f4-5f1d-462f-9213-3f2eb32aab51" />
<img width="1600" height="857" alt="SUCCESSFUL PING FROM PC1 TO PC0, PC2,   PC3" src="https://github.com/user-attachments/assets/ff31fcbe-9184-4761-af2f-e3cebf7ad851" />

