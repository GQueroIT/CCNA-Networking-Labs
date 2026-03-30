# Troubleshooting

---

## Issue 1: No Connectivity Between VLANs

### Problem
Devices connected to different switches but assigned to the same VLAN were unable to communicate.

### Cause
The trunk link between switches was not properly configured.

### Fix

interface gigabitEthernet 0/1
switchport mode trunk

### Verification

show interfaces trunk

Result:
- Trunk link became active
- VLAN traffic successfully passed between switches

---

## Issue 2: Incorrect VLAN Assignment

### Problem
A device was unable to communicate with other devices in the same VLAN.

### Cause
The access port was assigned to the wrong VLAN.

### Fix

interface fastEthernet 0/1
switchport access vlan 10

---

### Verification

show vlan brief

Result:
- Device appeared under the correct VLAN
- Connectivity restored

---

## Issue 3: Native VLAN Mismatch

### Problem
Trunk link was operational but showed inconsistent behavior.

### Cause
Native VLAN mismatch between switches.

### Fix

switchport trunk native vlan 99


### Verification

show interfaces trunk

Result:
- Native VLAN matched on both sides
- Trunk stabilized with no errors

---

## Lessons from Troubleshooting

- Always verify trunk links first when VLAN communication fails
- VLAN assignment errors are one of the most common issues
- Native VLAN mismatches can cause subtle connectivity problems
- Verification commands are critical in identifying misconfigurations