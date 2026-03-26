# Cisco IOS Basic Device Configuration

## Objective
This lab demonstrates how to access and configure a Cisco router using Cisco IOS. The objective was to configure an interface, assign IPv4 addressing, verify connectivity, and save the device configuration.

## Devices Used
- 1 Router (R1)
- 1 PC (PC1)

## Topology
A simple network consisting of a single router connected directly to a PC using a copper straight-through cable.

## Lab Steps

1. Built the topology in Packet Tracer (Router ↔ PC)
2. Connected devices using a copper straight-through cable
3. Accessed the router CLI via console
4. Entered privileged EXEC mode and global configuration mode
5. Configured the router interface with an IP address
6. Enabled the interface using `no shutdown`
7. Configured the PC with a static IPv4 address and default gateway
8. Verified connectivity using `ping`
9. Saved the configuration using `copy running-config startup-config`

## Addressing Table

| Device | Interface | IP Address | Subnet Mask | Default Gateway |
|--------|-----------|------------|-------------|-----------------|
| R1     | G0/0      | 192.168.1.1 | 255.255.255.0 | N/A |
| PC1    | NIC       | 192.168.1.2 | 255.255.255.0 | 192.168.1.1 |

## Skills Demonstrated
- Cisco IOS CLI navigation
- Privileged EXEC mode access
- Global configuration mode usage
- Interface configuration
- IPv4 addressing
- Interface activation using `no shutdown`
- Connectivity verification using ICMP (ping)
- Saving configuration to NVRAM

## Verification
The lab was verified using:
- `show ip interface brief`
- `show running-config`
- Successful ICMP ping from PC to router

## Outcome
The router interface was successfully configured and brought online. The PC was able to communicate with the router, confirming proper Layer 3 connectivity.

## Evidence

All screenshots for this lab are organized by step in the `/evidence` folder:

- Step 01: Topology creation and device connection
- Step 02: CLI access and interface configuration
- Step 03: Verification and IP configuration
- Final: Successful connectivity test (ping)

## Notes

This lab reinforced the importance of proper interface configuration and verification when establishing basic network connectivity. It also highlighted how critical it is to save configurations to prevent data loss after a reboot.