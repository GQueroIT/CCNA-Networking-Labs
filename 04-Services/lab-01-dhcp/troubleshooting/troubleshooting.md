# Troubleshooting Notes - Lab 01 DHCP Services

## Issue 01 - APIPA Addressing

### Problem
Several PCs initially received:
- 169.254.x.x addresses

instead of valid DHCP-assigned addresses.

### Root Cause
The DHCP requests were not successfully reaching the router DHCP server because the initial topology design was incorrect for Router-on-a-Stick implementation.

The original design attempted to:
- connect SW1 directly to R1
- connect SW2 directly to R1
- use separate physical interfaces while also configuring subinterfaces

This conflicted with Router-on-a-Stick architecture.

### Resolution
The topology was redesigned to use:
- one trunk connection between R1 and SW1
- one trunk connection between SW1 and SW2

R1 was configured using:
- G0/1.10
- G0/1.20

with:
- 802.1Q encapsulation
- VLAN-specific gateway IP addresses

After redesigning the topology, all PCs successfully received DHCP addresses.

--------------------------------------------------

## Issue 02 - Overlapping Subnet Error

### Problem
While configuring additional router interfaces, the following error occurred:

"192.168.10.0 overlaps with GigabitEthernet0/1.10"

### Root Cause
The router was being configured with multiple interfaces attempting to use the same subnet space.

Router-on-a-Stick only requires:
- one physical interface
- multiple logical subinterfaces

Creating additional routed interfaces within the same subnet caused an overlap conflict.

### Resolution
Removed the unnecessary interface configuration and continued using:
- G0/1.10
- G0/1.20

as the primary routed VLAN interfaces.

--------------------------------------------------

## Issue 03 - DHCP Pool Configuration Errors

### Problem
Several DHCP commands initially failed due to:
- incorrect CLI mode
- syntax mistakes
- attempting commands in subinterface mode

### Root Cause
DHCP configuration commands must be entered from:
- global configuration mode

Attempting DHCP commands from:
- subinterface configuration mode

generated invalid input errors.

### Resolution
Returned to global configuration mode using:

end
config t

Then successfully configured:
- excluded addresses
- DHCP pools
- default gateways
- DNS server settings

--------------------------------------------------

## Issue 04 - Trunking Verification

### Problem
Needed to verify whether VLAN traffic was successfully traversing between switches.

### Verification Commands Used

show interfaces trunk

show vlan brief

### Resolution
Confirmed:
- VLAN 10 active
- VLAN 20 active
- trunk ports forwarding VLAN traffic
- VLANs successfully propagated between switches

--------------------------------------------------

## Final Validation

The following validations were successfully completed:
- DHCP address assignment
- Inter-VLAN communication
- Gateway reachability
- Successful ping tests between VLANs
- Trunk verification
- DHCP binding verification

The final topology successfully demonstrated:
- VLAN segmentation
- DHCP services
- Router-on-a-Stick inter-VLAN routing
- Layer 2 trunking
- End-to-end network communication