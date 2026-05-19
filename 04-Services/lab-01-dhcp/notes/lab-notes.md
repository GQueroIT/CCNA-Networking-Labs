# Lab Notes - Lab 01 DHCP Services

## Overview
This lab focused on implementing DHCP services within a segmented VLAN environment using Router-on-a-Stick inter-VLAN routing. The objective was to dynamically assign IP addresses to devices across multiple VLANs while maintaining successful communication between separate broadcast domains.

The lab environment consisted of:
- 1 Router (R1)
- 2 Switches (SW1 and SW2)
- 2 VLANs
- 4 PCs

VLAN 10 was configured for the Sales department and VLAN 20 was configured for the HR department.

--------------------------------------------------

## VLAN Information

VLAN 10
- Name: Sales
- Network: 192.168.10.0/24
- Gateway: 192.168.10.1

VLAN 20
- Name: HR
- Network: 192.168.20.0/24
- Gateway: 192.168.20.1

--------------------------------------------------

## Router Configuration Summary

R1 was configured using Router-on-a-Stick topology through GigabitEthernet0/1.

Subinterfaces created:
- G0/1.10
- G0/1.20

Each subinterface used:
- 802.1Q encapsulation
- VLAN-specific gateway IP address

DHCP pools were created for:
- VLAN10
- VLAN20

Excluded address ranges were configured to reserve lower addresses for infrastructure devices.

--------------------------------------------------

## Switch Configuration Summary

SW1:
- Configured VLAN 10 and VLAN 20
- Configured access ports for end devices
- Configured trunk links to:
  - R1
  - SW2

SW2:
- Configured VLAN 10 and VLAN 20
- Configured access ports for end devices
- Configured trunk link to SW1

--------------------------------------------------

## DHCP Verification

All PCs successfully received:
- Dynamic IP addresses
- Correct subnet masks
- Correct default gateways

Verified DHCP assignment through:
- ipconfig
- Successful DHCP bindings on R1

--------------------------------------------------

## Connectivity Verification

Successful tests included:
- PC to gateway communication
- Inter-VLAN communication
- End-to-end connectivity between VLANs

Ping testing confirmed:
- Routing functionality
- VLAN trunk propagation
- DHCP operation

--------------------------------------------------

## Problems Encountered

### Initial Topology Design Issue
The original topology attempted to connect:
- SW1 directly to R1
- SW2 directly to R1

while also attempting to use Router-on-a-Stick subinterfaces.

This created confusion because Router-on-a-Stick is designed to use:
- ONE physical interface
- MULTIPLE logical subinterfaces
- ONE trunk connection

### APIPA Addressing
Several PCs initially received:
- 169.254.x.x addresses

This occurred because:
- DHCP requests were not reaching the correct router subinterfaces
- Trunking architecture was incomplete

### Overlapping Subnet Error
An overlapping subnet error occurred when attempting to configure:
- multiple interfaces
- within the same subnet space

The issue was resolved by redesigning the topology correctly using:
- a single trunk interface
- VLAN-tagged subinterfaces

--------------------------------------------------

## Lessons Learned

This lab reinforced several important networking concepts:
- Router-on-a-Stick architecture
- DHCP scope configuration
- VLAN segmentation
- Trunking operations
- Inter-VLAN routing
- DHCP troubleshooting methodology

One of the biggest lessons learned was understanding that Router-on-a-Stick relies on:
- one physical router interface
- multiple logical VLAN subinterfaces
- switch trunking to transport VLAN traffic

This lab also demonstrated how incorrect topology design can prevent DHCP communication and result in APIPA addressing.