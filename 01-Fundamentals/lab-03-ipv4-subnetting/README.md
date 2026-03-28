\# Lab 03 – IPv4 Subnetting with Inter-LAN Routing



\## Overview

In this lab, I implemented IPv4 subnetting using a /27 subnet mask to divide a /24 network into multiple smaller networks. Each subnet was assigned to a different LAN and connected through a router to allow inter-LAN communication.



This lab focused on applying subnetting concepts in a real network scenario and validating connectivity between multiple networks.



---



\## Objectives

\- Subnet a /24 network into smaller /27 networks

\- Assign IP addresses to router interfaces and end devices

\- Configure default gateways for each LAN

\- Verify connectivity within and across subnets

\- Understand how routing enables inter-LAN communication



---



\## Topology

The network consists of:

\- 1 Router (R1)

\- 3 LANs (A, B, C)

\- 3 PCs (one per subnet)



Each LAN is assigned its own subnet and connected to the router via separate interfaces.



---



\## IP Addressing Scheme



| Network | Subnet | Gateway | Host Range |

|--------|--------|--------|-----------|

| LAN A | 192.168.10.0/27 | 192.168.10.1 | .1 - .30 |

| LAN B | 192.168.10.32/27 | 192.168.10.33 | .33 - .62 |

| LAN C | 192.168.10.64/27 | 192.168.10.65 | .65 - .94 |



---



\## Configuration Summary

\- Router interfaces were assigned IP addresses based on each subnet

\- Each PC was configured with:

&nbsp; - IP address within its subnet

&nbsp; - Subnet mask (/27)

&nbsp; - Default gateway (router interface)



---



\## Verification



\### Interface Status

\- Verified using:



\### Connectivity Tests

\- Successful ping tests:

&nbsp; - PC → Default Gateway

&nbsp; - PC A → PC B

&nbsp; - PC A → PC C

&nbsp; - PC B → PC C



All inter-LAN communication was successful.



---



\## Key Takeaways

\- Subnetting allows efficient use of IP address space

\- Each subnet must have its own network ID and broadcast address

\- Default gateways are required for communication outside the local network

\- Routers enable communication between different subnets



---



\## Files Included

\- `/configs` → Router configuration

\- `/screenshots` → Step-by-step lab evidence

\- `/topology` → Packet Tracer file

\- `/notes` → Subnetting breakdown

\- `/troubleshooting` → Validation and troubleshooting steps

