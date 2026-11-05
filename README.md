# Secure Multi-Branch LAN Design – Cisco Packet Tracer

## Overview
A Layer 2 enterprise network simulation for a company with **3 branches** connected through a **central switch**. Each branch contains **3 departments** (IT, HR, Sales), each isolated in its own VLAN. Users can communicate with their own department in the other branches, but not with other departments.

The network is secured with port security and encrypted passwords, and all switches can be managed remotely via Telnet.

## Network Topology
![Topology]()

## Network Structure
| Device | Role | Location |
|--------|------|----------|
| Switch3 | VTP Server | Center |
| Switch0 | VTP Client | Branch 1 |
| Switch1 | VTP Client | Branch 2 |
| Switch2 | VTP Client | Branch 3 |

Each branch switch connects to the central switch through a trunk link.

## VLAN Design
| VLAN ID | Department |
|---------|------------|
| 10 | IT |
| 20 | Sales |
| 30 | HR |

## Technologies & Configuration

### VLANs & Trunking
- Separate VLAN per department in each branch
- Trunk links between the central switch and each branch switch to carry all VLANs

### VTP (VLAN Trunking Protocol)
- The central switch is configured as **VTP Server**; all branch switches are **VTP Clients**
- VLANs are created once on the server and automatically propagated to all branches

### Port Security
Configured on all access ports connected to department PCs:
- Maximum **1 MAC address** per port
- Violation mode: **shutdown**

### Device Security
- `service password-encryption` enabled to encrypt stored passwords
- Password protection on VTY lines

### Remote Management
- IP address assigned to **VLAN 1 interface** on each switch
- Telnet access enabled through VTY lines
- Console access to switches from PCs using console cables

## Verification
- Ping succeeds between PCs in the same VLAN across different branches
- Ping fails between PCs in different VLANs
- Connecting an unauthorized device to a secured port shuts the port down
- Telnet from a PC to each switch's VLAN 1 IP succeeds with the VTY password

## How to Run
1. Download the `.pkt` file from this repository
2. Open it using Cisco Packet Tracer
3. Test connectivity using ping between PCs

## Future Improvements
- Replace Telnet with SSH for encrypted remote access
- Add a dedicated management VLAN instead of VLAN 1
- Add Layer 3 routing for controlled inter-VLAN communication

## Author
[Ahmed Kamal Mustafa] - [www.linkedin.com/in/ahmed-kamal-161136381]
