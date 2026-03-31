# Lab 02 - Inter-VLAN Routing

## Objective

In this lab, I configured multiple VLANs across an enterprise-style switched network and implemented inter-VLAN routing using a router-on-a-stick design. The goal was to understand how separate VLANs communicate through a Layer 3 device while still maintaining segmentation at Layer 2.

---

## Technologies Used

- Cisco Packet Tracer
- Cisco IOS CLI
- VLAN configuration
- 802.1Q trunking
- Router-on-a-stick
- Basic connectivity testing

---

## Topology

- 1 router (R1)
- 2 switches (SW1 and SW2)
- 6 PCs
- VLAN 10 for Sales
- VLAN 20 for HR
- VLAN 30 for IT
- 1 trunk link between SW1 and SW2
- 1 trunk link between SW1 and R1

The network was built to simulate a small enterprise environment where departments are separated into different VLANs but still require communication through a router.

![Inter-VLAN Routing Topology](topology/intervlan-topology.png)

---

## IP Addressing

| Device | Interface | IP Address | Subnet Mask | Default Gateway |
|--------|-----------|------------|-------------|-----------------|
| R1 | G0/0.10 | 192.168.10.1 | 255.255.255.0 | N/A |
| R1 | G0/0.20 | 192.168.20.1 | 255.255.255.0 | N/A |
| R1 | G0/0.30 | 192.168.30.1 | 255.255.255.0 | N/A |
| PC1 | NIC | 192.168.10.10 | 255.255.255.0 | 192.168.10.1 |
| PC2 | NIC | 192.168.10.11 | 255.255.255.0 | 192.168.10.1 |
| PC3 | NIC | 192.168.20.10 | 255.255.255.0 | 192.168.20.1 |
| PC4 | NIC | 192.168.20.11 | 255.255.255.0 | 192.168.20.1 |
| PC5 | NIC | 192.168.30.10 | 255.255.255.0 | 192.168.30.1 |
| PC6 | NIC | 192.168.30.11 | 255.255.255.0 | 192.168.30.1 |

---

## VLAN Design

| VLAN | Name | Network |
|------|------|---------|
| 10 | SALES | 192.168.10.0/24 |
| 20 | HR | 192.168.20.0/24 |
| 30 | IT | 192.168.30.0/24 |

---

## Configuration Summary

### Switch Configuration
- Created VLAN 10, VLAN 20, and VLAN 30 on both switches
- Assigned access ports to the correct VLANs for each PC
- Configured the trunk link between SW1 and SW2
- Configured the trunk link between SW1 and R1

### Router Configuration
- Enabled the physical interface connected to SW1
- Configured router subinterfaces for each VLAN
- Applied `encapsulation dot1Q` for VLAN tagging
- Assigned the gateway IP address for each VLAN

---

## Verification

I verified the lab by checking VLAN assignments, trunk status, router subinterfaces, and successful end-to-end communication between devices in different VLANs.

### VLAN Verification
- `show vlan brief`
- Confirmed VLAN 10, VLAN 20, and VLAN 30 were active on both switches
- Confirmed access ports were assigned correctly

### Trunk Verification
- `show interfaces trunk`
- Confirmed the switch-to-switch and switch-to-router links were trunking
- Confirmed VLANs 10, 20, and 30 were allowed and active

### Router Verification
- `show ip interface brief`
- `show running-config`
- Confirmed all router subinterfaces were up and addressed correctly

### Connectivity Testing
- PC1 to PC4
- PC3 to PC6
- PC5 to PC1

All VLANs were able to communicate successfully through the router.

---

## Troubleshooting

During this lab, I ran into a few issues that helped reinforce the logic behind VLANs and inter-VLAN routing.

### Issue 1: ARP Request Failure
At one point, an ARP request timed out during testing. This showed that the device could not resolve the destination MAC address, which pointed me back to a Layer 2 issue rather than a routing issue.

### Issue 2: Wrong Router Subinterface Type
I initially tried to configure a FastEthernet subinterface on the router, but the actual connected interface was GigabitEthernet0/0. Once I corrected the interface type and built the subinterfaces on the proper physical interface, routing worked as expected.

### Issue 3: Switch Configuration Fixes
I also had to correct portions of the switch configuration to make sure VLAN membership and trunking behavior matched the lab design.

More details and screenshots are included in the troubleshooting folder.

---

## Notes

This lab helped me better understand the full path traffic takes when moving between VLANs. It also reinforced that when communication fails, I need to first identify whether the issue is happening at Layer 2 or Layer 3 before trying to fix it. This was a strong lab for tying VLANs, trunking, ARP behavior, and router-on-a-stick together in one working design.

---

## Files

- `README.md` - Main lab documentation
- `configs/router-config.txt` - Router configuration output
- `configs/switch-configs.txt` - Switch configuration output
- `notes/lessons-learned.md` - Key takeaways from the lab
- `troubleshooting/troubleshooting.md` - Issues encountered and fixes applied
- `topology/intervlan-routing-topology.png` - Network diagram
- `evidence/` - Verification screenshots organized by step