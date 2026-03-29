# Lab 04 — IPv6 Basics with Inter-Router Routing (Packet Tracer)

## Objective

In this lab, I configured IPv6 addressing across multiple LANs and implemented inter-router routing using static routes. The goal was to reinforce IPv6 fundamentals and validate end-to-end connectivity across a multi-router topology.

## Topology

- 2 Routers (R1, R2)
- 2 Switches (S1, S2)
- 2 PCs (PC1, PC2)

PC1 connects to R1, PC2 connects to R2, and both routers are connected via a WAN link.

## IPv6 Addressing Scheme

- LAN 1: 2001:DB8:A:1::/64
- LAN 2: 2001:DB8:A:2::/64
- WAN Link: 2001:DB8:A:12::/64

## Technologies Used

- IPv6 Addressing
- Static Routing
- Cisco IOS CLI
- Packet Tracer

---

## My Thought Process

While working through this lab, I approached it as a real troubleshooting scenario rather than following a fixed set of steps.

At first, I focused on getting basic IPv6 connectivity between each PC and its default gateway. When that failed, I verified interface status and realized that even with correct addressing, interfaces must be fully up (line protocol up) for communication to work.

After establishing local connectivity, I expanded the topology by introducing a second router. This required me to think about how traffic moves between networks instead of just within a single LAN.

I encountered multiple issues during this process:

- Incorrect IPv6 addressing on router interfaces
- Overlapping subnets assigned to different interfaces
- IPv6 routing not enabled on the routers
- Missing static routes between networks

Instead of restarting, I worked through each issue step by step by:

- Verifying interface configurations using `show ipv6 interface brief`
- Checking routing tables using `show ipv6 route`
- Testing connectivity incrementally using ping

Once I enabled IPv6 routing and configured static routes on both routers, I was able to achieve full end-to-end communication between PC1 and PC2.

This lab helped reinforce the importance of:

- Verifying Layer 1/2 before assuming routing issues
- Ensuring proper addressing before troubleshooting connectivity
- Understanding how routers make forwarding decisions in IPv6 networks

---

## Lessons Learned (Mistakes I Made)

During this lab, I ran into multiple issues that forced me to slow down and troubleshoot instead of just moving forward.

- I initially configured IPv6 addresses incorrectly on router interfaces, which caused connectivity failures even though the topology looked correct
- I assigned overlapping IPv6 networks across interfaces, which broke routing behavior
- I forgot to enable IPv6 routing (`ipv6 unicast-routing`), which prevented routers from forwarding traffic
- I assumed routing was the issue before verifying interface status and basic connectivity
- I had to troubleshoot failed pings step by step instead of jumping to conclusions

Working through these mistakes helped me better understand how IPv6 routing actually behaves in a real environment.

---

## Key Concepts

- Global Unicast Addressing
- Link-Local Addressing
- IPv6 Routing
- Static Routes
- Interface Configuration

---

## Commands Used

### Router Configuration (R1)

- enable
- configure terminal
- hostname R1
- ipv6 unicast-routing

- interface g0/0
- ipv6 address 2001:DB8:A:1::1/64
- no shutdown

- interface g0/1
- ipv6 address 2001:DB8:A:12::1/64
- no shutdown

---

### Router Configuration (R2)

- enable
- configure terminal
- hostname R2
- ipv6 unicast-routing

- interface g0/0
- ipv6 address 2001:DB8:A:2::1/64
- no shutdown

- interface g0/1
- ipv6 address 2001:DB8:A:12::2/64
- no shutdown

### Static Routing

- R1:
- ipv6 route 2001:DB8:A:2::/64 2001:DB8:A:12::2

- R2:
- ipv6 route 2001:DB8:A:1::/64 2001:DB8:A:12::1

### Verification Commands

- show ipv6 interface brief
- show ipv6 route
- ping 2001:DB8:A:1::1
- ping 2001:DB8:A:2::1
- ping 2001:DB8:A:12::1
- ping 2001:DB8:A:12::2

---

## Verification

- PC1 successfully pinged its default gateway
- PC2 successfully pinged its default gateway
- PC1 and PC2 achieved end-to-end connectivity across routers
- Routing tables confirmed proper path selection

## Evidence

### PC1 to Gateway Connectivity
![PC1 Gateway Ping](evidence/PC1%20Ping%20to%20Gateway%20Success.png)

### End-to-End Communication (PC1 to PC2)
![PC1 to PC2](evidence/PC1%20to%20PC2%20Communication.png)

### Routing Table (R1)
![R1 Routes](evidence/R1%20show%20route.png)

### Routing Table (R2)
![R2 Routes](evidence/R2%20show%20route.png)

---

## Key Takeaways

- IPv6 routing must be manually enabled using `ipv6 unicast-routing`
- Routers do not forward IPv6 traffic by default
- Each interface must be assigned a unique IPv6 subnet
- Static routes are required for communication between multiple routers
- Interface status must be verified before troubleshooting routing issues
- Addressing errors and overlapping networks can prevent connectivity

## Outcome

This lab successfully demonstrated IPv6 configuration and routing between multiple networks. I also troubleshooted interface issues, addressing conflicts, and routing errors to achieve full connectivity.