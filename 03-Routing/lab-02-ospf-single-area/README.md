# Lab 02 - OSPF Single Area

## Objective

The objective of this lab was to implement Open Shortest Path First (OSPF) in a single-area network and verify dynamic routing between routers. This lab replaces static routing with a dynamic routing protocol to allow automatic route exchange.

## Technologies Used

- Cisco Packet Tracer
- OSPF (Open Shortest Path First)
- IPv4 Addressing
- CLI (Command Line Interface)

## Topology

This lab consists of three routers connected in a linear topology. Each router connects to its own LAN, and OSPF Area 0 is used across all routers.

![OSPF Topology](topology/lab-02-ospf-single-area.png)

## IP Addressing

- R1 LAN: 192.168.10.0/24
- R2 LAN: 192.168.20.0/24
- R3 LAN: 192.168.30.0/24

- R1–R2 Link: 10.0.12.0/30
- R2–R3 Link: 10.0.23.0/30

## Configuration

Each router was configured with:

- Interface IP addressing
- OSPF process with a unique router ID
- Network statements to advertise connected networks into Area 0

Example (R1):

router ospf 1  
router-id 1.1.1.1  
network 192.168.10.0 0.0.0.255 area 0  
network 10.0.12.0 0.0.0.3 area 0  

## Verification

To validate that OSPF was functioning correctly, the following commands were used:

- show ip ospf neighbor  
- show ip route  
- show ip protocols  

The routing tables showed routes marked with "O", indicating they were learned through OSPF. Connectivity was verified using ping between networks.

## Key Takeaways

This lab demonstrated how OSPF allows routers to dynamically exchange routing information without manual route configuration. It reinforced the importance of correct network statements, wildcard masks, and verification commands.

## Repository Structure

lab-02-ospf-single-area  
configs  
evidence  
notes  
topology  
troubleshooting  
README.md  