## Lab 04: Department Network with VLANs, Static IP & DHCP

### Objective
Design and configure a multi-department network for a small company. Separate the Admin and Staff departments using VLANs, apply Static IP address for Admin devices, and use DHCP for Staff devices. Enable communication between both departments using Router-on-a-Stick.

### Topology
- 1 × 1941 Router
- 1 × 2960 Switch
- 6 × PCs (Admin-PC1, Admin-PC2, Staff-PC1, Staff-PC2, Staff-PC3, Staff-PC4)
- All PCs connected to the single Switch
- Switch connected to the Router via one trunk link (router-on-a-stick)

### VLAN Scheme
| VLAN | Name  | Purpose          | Network         |
|------|-------|------------------|-----------------|
| 10   | ADMIN | Admin Department | 192.168.10.0/24 |
| 20   | STAFF | Staff Department | 192.168.20.0/24 |

### IP Addressing Scheme
| Device      | Interface            | IP Address    | Subnet Mask   | Default Gateway | Method |
|-------------|-----------------------|---------------|---------------|------------------|--------|
| Admin-PC1   | FastEthernet0         | 192.168.10.10 | 255.255.255.0 | 192.168.10.1     | Static |
| Admin-PC2   | FastEthernet0         | 192.168.10.15 | 255.255.255.0 | 192.168.10.1     | Static |
| Router      | Gig0/0.10 (VLAN 10)   | 192.168.10.1  | 255.255.255.0 | -                | Static |
| Router      | Gig0/0.20 (VLAN 20)   | 192.168.20.1  | 255.255.255.0 | -                | Static |
| Staff-PC1–4 | FastEthernet0         | 192.168.20.x  | 255.255.255.0 | 192.168.20.1     | DHCP   |

### Steps Performed
1. Built the topology (1 Router + 1 Switch + 6 PCs)
2. Created VLAN 10 (ADMIN) and VLAN 20 (STAFF) on the switch
3. Assigned Admin PC ports to VLAN 10 and Staff PC ports to VLAN 20 as access ports
4. Configured the switch port connecting to the router as a trunk port
5. Configured static IP addresses on Admin-PC1 and Admin-PC2
6. Configured the router's physical interface (Gig0/0) with no IP, brought it up
7. Created subinterfaces Gig0/0.10 and Gig0/0.20 with 802.1Q encapsulation matching each VLAN
8. Configured a DHCP pool (STAFF_POOL) on the router for the Staff subnet
9. Set Staff PCs to obtain IP addresses automatically (DHCP)
10. Verified connectivity within and between VLANs using ping

### Key Concepts Learned
- A single switch cannot separate networks on its own — VLANs are required to create isolated broadcast domains on shared hardware
- Access ports carry traffic for one VLAN; trunk ports carry multiple VLANs simultaneously using 802.1Q tagging
- A physical router interface can only hold one IP address, so router-on-a-stick uses subinterfaces to give each VLAN its own gateway over a single physical link
- DHCP requests are broadcast traffic and only reach the correct pool once the requesting port is tagged to the matching VLAN
- Order of operations matters: VLANs must exist, and ports must be assigned before DHCP will function correctly

### Troubleshooting Notes
- Initially assigned an IP directly to the physical Gig0/0 interface instead of to the subinterfaces — this had to be removed (`no ip address`) before the subinterfaces could take over addressing duties for each VLAN
- Staff PCs first received APIPA addresses (169.254.x.x) because their switch ports were still in the default VLAN 1 — VLANs 10 and 20 had been created but never assigned to any ports
- Fixed by assigning the correct switch ports to VLAN 10 and VLAN 20 with `switchport access vlan`, after which DHCP began working correctly
- Ran `show vlan brief` on the switch to confirm each PC port was mapped to the correct VLAN before retesting

### Verification
- Admin-PC1 and Admin-PC2 (VLAN 10) communicated successfully with each other and their gateway
- Staff-PC1–4 received valid 192.168.20.x addresses automatically from the DHCP pool
- Admin PCs successfully pinged Staff PCs and vice versa, confirming inter-VLAN routing through the router subinterfaces
- First cross-VLAN ping showed 1 dropped packet due to ARP resolution delay — subsequent pings passed with 0% loss

### Screenshots
- Full Network Topology 
<img width="1600" height="854" alt="NETWORK TOPOLOGY" src="https://github.com/user-attachments/assets/4efb4ae2-f679-43d9-a032-949474c154b3" />

- Switch trunk port configuration and `show vlan brief` output (ports mapped to VLAN 10 / VLAN 20)
<img width="1600" height="854" alt="SWITCH CLI TRUNK CONFIGURATION   VLAN BRIEF" src="https://github.com/user-attachments/assets/974afc53-42c3-4e97-8ef7-7030827b406b" />

- Router subinterface configuration (PHYSICAL INTERFACE, SUBINTERFACE & DHCP)
<img width="1600" height="857" alt="CLI CONFIGURATION ON ROUTER FOR ROUTER&#39;S PHYSICAL INTERFACE,SUBINTERFACE FOR VLANS   DHCP" src="https://github.com/user-attachments/assets/4702e02a-1700-478b-878e-fa4f6cc86e8c" />

- Static IP configuration on Admin-PC1
<img width="1600" height="850" alt="STATIC IP ADDRESS CONFIGURATION ON ADMIN PC" src="https://github.com/user-attachments/assets/6a3e0b42-3dca-422d-9442-17fea01ad7d7" />

- DHCP-assigned IP on a Staff PC
<img width="1600" height="852" alt="AUTOMATIC DHCP IP CONFIGURATION ON STAFF PC" src="https://github.com/user-attachments/assets/af40f757-afbe-48a2-a6a3-6b1393875e3d" />

- Successful ping: Admin PC ↔ Staff PC (inter-VLAN)
<img width="1600" height="854" alt="SUCCESSFUL PING FROM ADMIN PC 1 TO STAFF PC 1   2" src="https://github.com/user-attachments/assets/944f2f37-6859-425d-93ba-76a480e8de04" />
<img width="1600" height="856" alt="SUCCESSFUL PING FROM STAFF PC 1 TO ADMIN PC 1   2" src="https://github.com/user-attachments/assets/c78e55af-4d8f-413a-b066-e4e20c46dd2b" />

