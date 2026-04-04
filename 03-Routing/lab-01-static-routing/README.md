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

## Evidence

### Initial Connectivity Failure

![ICMP Failure](evidence/01-icmp-failure-initial.png)

The initial ping attempt failed due to missing routing information and ARP resolution.

---

### Successful Connectivity

![ICMP Success](evidence/02-icmp-success.png)

After proper configuration and ARP resolution, communication was successfully established.

---

### PC Configuration

![PC1 Config](evidence/03-pc1-ip-configuration.png)  
![PC1 Gateway](evidence/04-pc1-default-gateway.png)

![PC2 Config](evidence/05-pc2-ip-configuration.png)  
![PC2 Gateway](evidence/06-pc2-default-gateway.png)

---

### Router Configuration

#### R1

![R1 Initial](evidence/07-r1-initial-configuration.png)  
![R1 Link Setup](evidence/08-r1-point-to-point-link.png)  
![R1 Fix](evidence/09-r1-corrected-configuration.png)  
![R1 Running Config](evidence/10-r1-running-config.png)  
![R1 Routing Table](evidence/11-r1-routing-table.png)

---

#### R2

![R2 Setup](evidence/12-r2-initial-configuration.png)  
![R2 Final](evidence/13-r2-final-configuration.png)  
![R2 Routing](evidence/14-r2-routing-table.png)

---

#### R3

![R3 Setup](evidence/15-r3-initial-configuration.png)  
![R3 Adjustments](evidence/16-r3-adjustments.png)  
![R3 Issue](evidence/17-r3-connectivity-issue.png)  
![R3 Route Added](evidence/18-r3-static-route-added.png)  
![R3 Fix](evidence/19-r3-route-correction.png)  
![R3 Final](evidence/20-r3-final-configuration.png)  
![R3 Routing](evidence/21-r3-routing-table.png)

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