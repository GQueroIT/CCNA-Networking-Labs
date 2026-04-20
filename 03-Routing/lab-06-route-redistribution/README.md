# Lab 06 - Route Redistribution

## Objective
This lab demonstrates how to connect two separate routing domains by using route redistribution on a boundary router. On the left side of the topology, OSPF was used to advertise internal networks across R1, R2, and R3. On the right side, EIGRP was used between R3 and R4. The main objective was to configure R3 to redistribute routes between both protocols so that full end-to-end communication could take place across the topology.

---

## Technologies Used
- Cisco Packet Tracer
- OSPF
- EIGRP
- Route Redistribution
- Loopback Interface
- CLI Verification and Troubleshooting

---

## Topology
The topology was built with four routers and two endpoints.

- R1 represented the OSPF-side edge router with a local LAN
- R2 acted as an internal OSPF router and also hosted a loopback network
- R3 acted as the redistribution router between OSPF and EIGRP
- R4 represented the EIGRP-side edge router with a local LAN
- PC1 was placed behind R1
- PC2 was placed behind R4

### Topology Flow
PC1 -> R1 -> R2 -> R3 -> R4 -> PC2

---

## IP Addressing Plan

| Device | Interface | IP Address | Subnet Mask |
|---|---|---:|---:|
| PC1 | NIC | 192.168.10.10 | 255.255.255.0 |
| R1 | G0/0 | 192.168.10.1 | 255.255.255.0 |
| R1 | G0/1 | 10.0.12.1 | 255.255.255.252 |
| R2 | G0/0 | 10.0.12.2 | 255.255.255.252 |
| R2 | G0/1 | 10.0.23.1 | 255.255.255.252 |
| R2 | Lo0 | 192.168.20.1 | 255.255.255.0 |
| R3 | G0/0 | 10.0.23.2 | 255.255.255.252 |
| R3 | G0/1 | 10.0.34.1 | 255.255.255.252 |
| R4 | G0/0 | 10.0.34.2 | 255.255.255.252 |
| R4 | G0/1 | 192.168.40.1 | 255.255.255.0 |
| PC2 | NIC | 192.168.40.10 | 255.255.255.0 |

### Default Gateways
- PC1 -> 192.168.10.1
- PC2 -> 192.168.40.1

---

## Routing Design

### OSPF Domain
OSPF process 1 was used across the left side of the topology:
- R1
- R2
- R3 interface facing R2

The OSPF domain advertised:
- 192.168.10.0/24
- 192.168.20.0/24
- 10.0.12.0/30
- 10.0.23.0/30

### EIGRP Domain
EIGRP autonomous system 100 was used across the right side of the topology:
- R3 interface facing R4
- R4

The EIGRP domain advertised:
- 10.0.34.0/30
- 192.168.40.0/24

### Redistribution Point
R3 served as the routing boundary between both protocols. Redistribution was configured in both directions so that:
- OSPF routes were injected into EIGRP
- EIGRP routes were injected into OSPF

---

## Configuration Summary

### R1
- Configured local LAN interface for PC1
- Configured transit link to R2
- Enabled OSPF for the LAN and transit network

### R2
- Configured both transit interfaces
- Created Loopback0 to simulate an additional internal LAN
- Advertised all connected OSPF networks

### R3
- Participated in both OSPF and EIGRP
- Formed the redistribution boundary
- Redistributed EIGRP into OSPF
- Redistributed OSPF into EIGRP using an explicit metric

### R4
- Configured transit link to R3
- Configured local LAN interface for PC2
- Enabled EIGRP for the transit and LAN networks

---

## Verification
The following verification steps were used to confirm successful operation:

### Neighbor Verification
- `show ip ospf neighbor`
- `show ip eigrp neighbors`

### Routing Table Verification
- `show ip route`
- `show ip route ospf`
- `show ip route eigrp`

### End-to-End Testing
- Successful ping from PC1 to PC2
- Successful reachability across the redistribution boundary
- Traceroute confirmed the expected traffic path through the routed topology

---

## Evidence
The `evidence` folder should include screenshots that validate the major stages of the lab, such as:
- Topology overview
- OSPF configuration
- Loopback configuration on R2
- EIGRP configuration on R4
- Redistribution configuration on R3
- Routing tables after redistribution
- Successful ping between endpoints
- Traceroute across the topology

---

## Troubleshooting Notes
During validation, connectivity from PC1 to the remote endpoint initially failed even though the OSPF side of the topology was operating correctly. This was expected because both routing domains were still isolated from one another. The issue was resolved by configuring bidirectional route redistribution on R3.

This lab reinforced the importance of validating each routing domain independently before troubleshooting end-to-end failures across the redistribution boundary.

---

## Files
- `README.md`
- `configs/r1-config.txt`
- `configs/r2-config.txt`
- `configs/r3-config.txt`
- `configs/r4-config.txt`
- `notes/lessons-learned.md`
- `troubleshooting/troubleshooting.md`
- `topology/lab-06-route-redistribution.pkt`

---

## What This Lab Demonstrates
This lab demonstrates that I can build separate routing domains, configure a boundary router that participates in multiple routing protocols, implement bidirectional route redistribution, and verify end-to-end traffic flow across the network. It also shows that I can troubleshoot routing problems logically by isolating protocol domains before applying the final redistribution configuration.