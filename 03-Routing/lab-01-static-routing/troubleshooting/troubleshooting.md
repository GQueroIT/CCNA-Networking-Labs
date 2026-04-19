# Troubleshooting

During this lab, I encountered several issues that impacted end-to-end connectivity. Each issue required isolating the problem and validating configurations step-by-step to determine the root cause.

---

## Issue 1: Initial Connectivity Failure

The first ping attempt between PC1 and PC2 failed. At first glance, this appeared to be a routing issue, but further testing showed that the network configuration was correct.

### Root Cause
The failure was due to ARP (Address Resolution Protocol) not yet resolving the MAC address of the next-hop device.

### Resolution
After allowing ARP to complete and sending additional ping requests, connectivity was successfully established.

---

## Issue 2: Incorrect Next-Hop Address

At one point, a static route was configured using the router’s own IP address as the next-hop instead of the neighboring router.

### Root Cause
The route pointed to the local interface instead of the correct next-hop router, preventing traffic from being forwarded properly.

### Resolution
The static route was corrected to use the adjacent router’s IP address as the next-hop, restoring proper routing behavior.

---

## Issue 3: Duplicate IP Address

A duplicate IP address was accidentally assigned to two interfaces on the same network segment.

### Root Cause
Both routers were configured with the same IP address on a point-to-point link, causing a conflict and preventing proper communication.

### Resolution
The incorrect IP address was removed and reassigned correctly, ensuring each interface had a unique address.

---

## Issue 4: Missing Return Path

Connectivity initially failed even after forward routing was configured correctly.

### Root Cause
The destination router did not have a route back to the source network, preventing return traffic from reaching the original sender.

### Resolution
A static route was added on the destination router to provide a return path, allowing full bidirectional communication.

---

## Troubleshooting Approach

To resolve these issues, I followed a structured process:

- Verified interface status using `show ip interface brief`  
- Checked routing tables using `show ip route`  
- Tested connectivity incrementally using `ping`  
- Validated IP addressing and default gateways on end devices  

This step-by-step approach made it easier to isolate issues and confirm when each problem was resolved.