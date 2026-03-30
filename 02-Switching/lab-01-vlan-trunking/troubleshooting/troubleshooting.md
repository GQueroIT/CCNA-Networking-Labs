# Troubleshooting

## Issue 1: No Connectivity Across Switch Link

### Problem
During initial testing, devices connected to different switches were unable to communicate even though they were assigned to the same VLAN.

### Cause
The link between the switches was not operating as a trunk, so VLAN traffic was not being carried between switches.

### Fix

interface gigabitEthernet 0/1
switchport mode trunk

### Verification

show interfaces trunk

Result:
- The trunk interface appeared in the output
- VLAN traffic was successfully carried between switches
- Devices in the same VLAN across switches were able to communicate

---

## Issue 2: Incorrect VLAN Assignment

### Problem
A device was not able to communicate with other devices in the same VLAN.

### Cause
The access port was assigned to the wrong VLAN.

### Fix

interface fastEthernet 0/1
switchport mode access
switchport access vlan 10

### Verification

show vlan brief

Result:
- The interface appeared under the correct VLAN
- VLAN membership aligned with the topology
- Communication was restored

---

## Issue 3: Failed Connectivity During Validation

### Problem
End-to-end connectivity tests initially failed during validation.

### Cause
The issue required verification across multiple areas, including VLAN membership, trunk configuration, and device addressing.

### Fix
Reviewed and validated:
- VLAN assignments on all access ports
- Trunk configuration between switches
- End-device IP configuration

### Verification

show vlan brief
show interfaces trunk
ping <destination-ip>

Result:
- VLAN configuration matched across switches
- Trunk was confirmed operational
- Connectivity behaved as expected based on VLAN segmentation

---

## Lessons from Troubleshooting

- Trunk configuration should be verified first when VLAN communication fails across switches
- Incorrect VLAN assignments are a common cause of connectivity issues
- End-to-end testing helps isolate whether the issue is Layer 2 or host configuration related
- Verification commands are critical for identifying and confirming misconfigurations