# Lab 01 – Static Routing

## Objective

The objective of this lab was to configure static routing between multiple routers to enable end-to-end communication across different networks. This lab focuses on understanding how routers make forwarding decisions using manually defined routes and how misconfigurations impact connectivity.

---

## What This Lab Demonstrates

- Configuration of static routes between routers  
- Understanding of next-hop IP addressing  
- End-to-end connectivity across multiple subnets  
- Troubleshooting routing issues and incorrect configurations  
- Interaction between Layer 2 (ARP) and Layer 3 (IP routing)  

---

## Topology

![Network Topology](evidence/22-network-topology.png)

---

## IP Addressing

| Device | Interface | IP Address | Subnet Mask |
|--------|----------|------------|-------------|
| R1     | G0/0     | 192.168.10.1 | 255.255.255.0 |
| R1     | G0/1     | 10.0.12.1    | 255.255.255.252 |
| R2     | G0/0     | 10.0.12.2    | 255.255.255.252 |
| R2     | G0/1     | 10.0.23.2    | 255.255.255.252 |
| R3     | G0/0     | 10.0.23.1    | 255.255.255.252 |
| R3     | G0/1     | 192.168.30.1 | 255.255.255.0 |
| PC1    | NIC      | 192.168.10.10 | 255.255.255.0 |
| PC2    | NIC      | 192.168.30.10 | 255.255.255.0 |

---

## Configuration

### Static Routing

Example static route:

ip route 192.168.30.0 255.255.255.0 10.0.12.2

Each router was configured with routes pointing to the next-hop IP address to reach remote networks.

---

## Implementation Summary

The lab was built using a three-router topology with two end networks. Static routes were configured on each router to enable communication between the networks.

PC1 and PC2 were configured with correct IP addressing and default gateways pointing to their respective routers. Router interfaces were assigned IP addresses based on point-to-point subnetting between each device.

Static routes were then configured on each router to define paths to remote networks. Each route specified the destination network along with the correct next-hop IP address.

---

## Verification

Connectivity was tested using ICMP (ping) between end devices.

Initial testing resulted in a failed ping. This behavior was expected due to ARP (Address Resolution Protocol) not yet resolving the MAC address of the next-hop device. After ARP resolution completed, subsequent ping attempts were successful.

Verification steps included:

- Confirming interface status with `show ip interface brief`  
- Reviewing routing tables using `show ip route`  
- Testing end-to-end connectivity using `ping`  

Successful communication between PC1 and PC2 confirmed that routing was correctly configured across all routers.

---

## Router Configuration Summary

Each router was configured with:

- Proper IP addressing on all interfaces  
- Static routes pointing to remote networks  
- Correct next-hop IP addresses for packet forwarding  

Full configurations are available in:

configs/router-configs.txt

---

## Troubleshooting

During this lab, several issues were encountered and resolved:

- Incorrect next-hop IP addresses in static routes  
- Missing routes preventing end-to-end connectivity  
- Misconfigured interfaces  
- Initial ICMP failures caused by ARP resolution delay  

The most important observation was that the first ping attempt may fail because ARP (Address Resolution Protocol) has not yet resolved the MAC address of the next-hop device. Once ARP entries are populated, subsequent communication succeeds.

---

## Key Takeaways

This lab reinforced how critical correct routing information is for network communication. Even a single incorrect static route can break connectivity across the entire topology. It also highlighted how Layer 2 and Layer 3 interact, specifically how ARP plays a role in initial communication attempts.

Understanding static routing provides the foundation for more advanced routing protocols such as OSPF and EIGRP, where route learning becomes dynamic instead of manually configured.

---

## Lessons Learned

This lab reinforced the importance of precision when working with static routing. Unlike dynamic routing protocols, static routes require complete accuracy in both destination networks and next-hop addresses. Even a minor misconfiguration can result in total loss of connectivity across the topology.

One of the most important insights from this lab was observing how initial connectivity failures are not always caused by incorrect configurations, but rather by normal network behavior such as ARP resolution. The first ICMP request may fail while the device resolves the MAC address of the next-hop router, but subsequent attempts succeed once the ARP table is populated.

Additionally, this lab strengthened my understanding of how routers build and rely on their routing tables to make forwarding decisions. Verifying routes using commands such as `show ip route` proved to be essential in identifying and correcting issues.

---

## What I Would Do Differently

If I were to approach this lab again, I would take a more structured validation approach during configuration. Instead of configuring all devices first and testing at the end, I would verify connectivity incrementally after each major step.

For example, I would:
- Verify interface status and IP configuration immediately after setup  
- Test point-to-point connectivity between routers before adding static routes  
- Validate routing tables after each route is added  
- Use targeted ping and traceroute tests to isolate issues faster  

This approach would reduce troubleshooting time and make it easier to identify exactly where a failure occurs.

Moving forward, I will apply this incremental validation method to all networking labs and real-world scenarios to improve efficiency and accuracy.