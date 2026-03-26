# Concepts

## Cisco IOS
Cisco IOS (Internetwork Operating System) is the command-line operating system used to configure and manage Cisco networking devices.

## CLI Modes
Cisco devices use different CLI modes:
- User EXEC (`>`)
- Privileged EXEC (`#`)
- Global Configuration (`(config)#`)
- Interface Configuration (`(config-if)#`)

Each mode allows different levels of control.

## Interface Configuration
Network interfaces must be configured with an IP address and enabled before they can pass traffic, without this device cannot participate in layer 3 communication. 

## IPv4 Addressing
Devices must be in the same subnet to communicate directly. If they are not, traffic must be sent to a default gateway fpr routing. In this lab, both the router and PC were configured within the 192.168.1.0/24 network.

## Default Gateway
The default gateway is used by a host to communicate with devices outside its local network. In this lab, the router acts as the gateway.

## no shutdown
Interfaces on Cisco routers are administratively disabled by default. The `no shutdown` command enables the interface.

## Saving Configuration
Configurations are stored in RAM by default. To make them persistent, they must be saved to NVRAM using:
copy running-config startup-config

## ICMP (Ping)
The ping command uses ICMP (Internet Control Message Protocol) to test connectivity between devices. A successful ping confirms that Layer 3 communication is working properly.