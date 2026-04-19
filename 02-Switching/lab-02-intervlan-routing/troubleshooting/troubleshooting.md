# Troubleshooting

## Overview

During this lab, I ran into multiple issues that required me to troubleshoot both Layer 2 and Layer 3 configurations. Each issue helped reinforce how traffic actually flows through a network and where failures can occur.

---

## Issue 1: ARP Request Failure (Layer 2 Problem)

### Problem

When attempting to ping another device, the ARP request timed out and the packet was dropped. The device could not resolve the destination MAC address.

### What This Meant

This indicated a Layer 2 issue. Since ARP is a broadcast process, the failure meant the devices were not in the same broadcast domain or VLAN.

### Root Cause

- Incorrect VLAN assignment on switch ports
- VLAN mismatch between devices

### Fix

- Verified VLAN configuration using:
  show vlan brief
- Ensured both devices were assigned to the same VLAN
- Confirmed VLAN existed on the switch

### Evidence

- arp-request-fail.png
- pc1-pc2-ping-fail.png

---

## Issue 2: Inter-VLAN Routing Not Working (Layer 3 Problem)

### Problem

Devices in different VLANs could not communicate even though VLAN configuration and trunking were correct.

### What This Meant

Traffic was reaching the router, but the router was not properly routing between VLANs.

### Root Cause

- Incorrect subinterface configuration
- Attempted to use the wrong interface type

### Fix

- Identified the correct physical interface (GigabitEthernet0/0)
- Created subinterfaces:
  interface g0/0.10
  interface g0/0.20
  interface g0/0.30
- Applied encapsulation:
  encapsulation dot1Q <vlan-id>
- Assigned correct IP addresses to each subinterface

### Evidence

- router-config.png
- router-ip-interface-brief.png
- router-running-config.png

---

## Issue 3: Switch Configuration Corrections

### Problem

Some VLAN and trunk configurations were not behaving as expected during initial testing.

### Root Cause

- Incomplete or incorrect switch configuration
- Trunk or VLAN inconsistencies

### Fix

- Rechecked trunk links:
  show interfaces trunk
- Verified VLAN assignments:
  show vlan brief
- Corrected configuration where needed

### Evidence

- SW1-config-fix.png
- SW2-config-fix.png

---

## Key Takeaway

This lab reinforced that troubleshooting should follow a structured approach. Before assuming routing issues, I first need to confirm Layer 2 connectivity is working. Once switching is verified, then I can move up to Layer 3 and validate routing behavior.