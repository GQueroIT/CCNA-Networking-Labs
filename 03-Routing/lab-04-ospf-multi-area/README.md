# Lab 05 - OSPF Multi-Area Design

## Objective
The objective of this lab is to design and implement a multi-area OSPF topology while integrating VLANs and router-on-a-stick. This lab builds on previous routing and switching concepts and introduces a more structured, enterprise-style network design using multiple OSPF areas.

---

## Technologies Used
- Cisco Packet Tracer
- VLANs
- Trunking (802.1Q)
- Router-on-a-Stick
- OSPF (Multi-Area)
- IPv4 Addressing (/30 point-to-point links)

---

## Topology

![Topology](./topology/ospf-routing-topology.pkt)

---

## IP Addressing

### VLAN Networks
- VLAN 10: 10.10.10.0/24
- VLAN 20: 10.20.20.0/24

### Point-to-Point Links
- R1–R2: 10.0.0.0/30
- R2–R3: 10.0.0.4/30
- R3–R4: 10.0.0.8/30

---

## Configuration Summary

### Switching
- VLAN 10 and VLAN 20 created
- Access ports assigned to appropriate VLANs
- Trunk links configured between switches and routers
- Allowed VLANs explicitly defined on trunks

### Routing
- Router-on-a-stick implemented on edge routers
- Subinterfaces configured with 802.1Q encapsulation
- Default gateways provided for each VLAN

### OSPF
- OSPF process 1 configured on all routers
- Area 0 used as backbone
- Area 1 implemented for segmented routing
- R3 configured as the Area Border Router (ABR)

---

## Verification

### Key Commands Used
show ip interface brief  
show ip route  
show ip ospf neighbor  
show ip protocols  
show vlan brief  
show interfaces trunk  

### Expected Results
- All router interfaces are up/up
- OSPF neighbors reach FULL state
- VLANs are correctly assigned
- Trunks are carrying VLAN 10 and 20
- End devices can communicate across VLANs and areas

---

## Notes

This lab demonstrates how multiple networking concepts can be combined into a single topology. It highlights the importance of structured design, correct OSPF area placement, and proper VLAN and trunk configuration when building a scalable network.

---

## Troubleshooting

See:  
./troubleshooting/troubleshooting.md  

---

## Lessons Learned

See:  
./notes/lessons-learned.md  

---

## Files
- configs/ → Device configurations  
- evidence/ → Screenshots and verification  
- topology/ → Packet Tracer file  