# Lab 03 — IPv4 Subnetting with Inter-LAN Routing (Packet Tracer)

## Objective
In this lab, I implemented IPv4 subnetting using a /27 subnet mask to divide a /24 network into multiple smaller networks. Each subnet was assigned to a different LAN and connected through a router to allow inter-LAN communication.

The goal was to reinforce subnetting concepts and validate communication between multiple networks using proper IP addressing and routing.

---

## Technologies Used
- Cisco Packet Tracer
- IPv4 Addressing
- Subnetting (/27)
- ICMP (Ping)
- Routing (Inter-LAN Communication)

---

## Topology
- 1 Router (R1)
- 3 LANs (A,B,C)
- 6 PCs (2 per subnet)
### Network Topology
![Network Topology](./evidence/step-01-topology/Successful%20Topology%20Scheme.png)

---

## IP Addressing

| Network | Subnet | Gateway | Host Range |
|--------|--------|--------|-----------|
| LAN A | 192.168.10.0/27 | 192.168.10.1 | .1 - .30 |
| LAN B | 192.168.10.32/27 | 192.168.10.33 | .33 - .62 |
| LAN C | 192.168.10.64/27 | 192.168.10.65 | .65 - .94 |

---

## Configuration
- Router interfaces were configured with IP addresses from each subnet
- Each PC was assigned:
  - IP address within its subnet
  - Subnet mask (/27)
  - Default gateway (router interface)

Router configuration is available in `/configs`.

---

## Verification

### Interface Status
![show ip interface brief](./evidence/step-03-show-ip-int-brief/IP%20Interface%20Brief%20Command%20Router.png)
Verified using:

### Connectivity Tests
- Successful ping to default gateway from each PC
- Successful communication between all LANs (A ↔ B ↔ C)

#### LAN A to Gateway / General Ping Validation
![LAN A Ping](./evidence/step-07-ping-tests/LAN%20A%20Ping.png)

#### LAN A to LAN B
![LAN B Ping](./evidence/step-07-ping-tests/LAN%20B%20Ping.png)

#### LAN A to LAN C
![LAN C Ping](./evidence/step-07-ping-tests/LAN%20C%20Ping.png)

All inter-LAN routing was confirmed operational.

---

## Notes
Subnetting this /24 network into /27 blocks reinforced:
- Network boundaries
- Usable host ranges
- Broadcast addresses
- Default gateway placement

Detailed notes available in `/notes`.

---

## Troubleshooting
No major issues encountered during this lab.

Validation included:
- Verifying interface status
- Confirming IP addressing and subnet masks
- Checking default gateway configuration
- Testing connectivity across all subnets

Troubleshooting notes available in `/troubleshooting`.

---

## Files
- `/configs` → Router configuration
- `/evidence` → Step-by-step lab evidence
- `/topology` → Packet Tracer file
- `/notes` → Subnetting breakdown
- `/troubleshooting` → Validation notes