# Troubleshooting Log

## Issue 1 — PC could not ping default gateway

**Symptoms:**
- PC was unable to reach the default gateway
- Ping requests were failing

**Root Cause:**
- Router interface was not fully up (administratively down)

**Verification:**
- Checked interface status on router
- Observed interface was down/down

**Resolution:**
- Enabled interface using `no shutdown`
- Confirmed line protocol came up

**Result:**
- PC successfully pinged default gateway
- Network connectivity restored

---

## Issue 2 — Incorrect IPv6 addressing

**Symptoms:**
- Devices could not communicate across the network
- IPv6 pings were failing between LAN segments

**Root Cause:**
- Router interface was assigned to the wrong IPv6 subnet

**Verification:**
- Compared configured IPv6 addresses with topology design
- Identified mismatch between LAN networks and interface assignments

**Resolution:**
- Reassigned correct IPv6 addresses to match LAN segments

**Result:**
- Devices were able to communicate successfully
- IPv6 connectivity restored across the network

---

## Issue 3 — IPv6 routing not working

**Symptoms:**
- Inter-network communication failed
- Devices could only reach local network

**Root Cause:**
- IPv6 routing was not enabled on the router

**Verification:**
- Checked running configuration
- Confirmed absence of IPv6 routing configuration

**Resolution:**
- Enabled IPv6 routing using `ipv6 unicast-routing`

**Result:**
- Routing between networks became operational
- Full IPv6 connectivity achieved