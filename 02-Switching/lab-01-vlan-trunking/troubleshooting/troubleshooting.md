## Troubleshooting

Detailed troubleshooting scenarios, including failures, fixes, and verification steps, are documented in the `troubleshooting` folder.

This includes:
- VLAN misconfiguration issues
- Trunk configuration validation
- End-to-end connectivity testing

---

## Issue 1: No Connectivity Across the Switch Link

### Problem
Devices that should have been able to communicate across the switch-to-switch connection were not passing traffic as expected.

### Cause
The link between the switches was not functioning as a trunk, so VLAN traffic was not being carried correctly between switches.

### Fix

interface gigabitEthernet 0/1
switchport mode trunk

### Verification

show interfaces trunk

Result:
- The trunk link appeared in the trunk table
- VLAN traffic was able to pass across the switch link

---

## Issue 2: Incorrect VLAN Assignment

### Problem
A device could not communicate with the correct VLAN segment.

### Cause
The access port was assigned to the wrong VLAN.

### Fix

interface fastEthernet 0/1
switchport mode access
switchport access vlan 10

### Verification

show vlan brief

Result:
- The port appeared under the correct VLAN
- VLAN membership matched the intended design

---

## Issue 3: End-to-End Connectivity Failure During Validation

### Problem
Initial connectivity testing did not work as expected during validation.

### Cause
The issue required validation of VLAN membership, trunk status, and device addressing to confirm where communication was failing.

### Fix
The configuration was reviewed and corrected by checking:
- VLAN assignments on access ports
- Trunk operation between switches
- End-device IP configuration

### Verification

show vlan brief
show interfaces trunk
ping <destination-ip>

Result:
- VLAN membership matched the topology
- Trunking was confirmed operational
- Connectivity behavior matched the intended lab design

---

## Lessons from Troubleshooting

- Trunk verification should be one of the first checks when VLAN traffic fails across switches
- Incorrect access port VLAN assignments can break communication quickly
- End-to-end testing helps confirm whether the issue is with switching, VLAN membership, or host addressing
- Verification commands are just as important as the configuration itself