# Troubleshooting Log

## Issue 1 — PC could not ping default gateway

Cause:
- Router interface was not fully up

Fix:
- Enabled interfaces using no shutdown
- Verified line protocol was up

---

## Issue 2 — Incorrect IPv6 addressing

Cause:
- Router interface was assigned to the wrong subnet

Fix:
- Reassigned correct IPv6 addresses matching LAN networks

---

## Issue 3 — IPv6 routing not working

Cause:
- IPv6 routing not enabled on router

Fix:
- Enabled using:
  ipv6 unicast-routing

---

## Issue 4 — Overlapping IPv6 networks

Cause:
- Same subnet assigned to multiple interfaces

Fix:
- Assigned unique networks to each interface

---

## Issue 5 — No connectivity between LANs

Cause:
- Missing static routes

Fix:
- Configured static routes on both routers

Result:
- End-to-end communication successfully established