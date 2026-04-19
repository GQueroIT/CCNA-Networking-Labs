# Verification Summary

## Objective Verification
The goal of this lab was to successfully configure VLAN segmentation and establish trunking between switches to allow inter-VLAN traffic across multiple devices.

All configurations were tested and verified using Cisco IOS show commands and end-to-end connectivity testing.

---

## VLAN Verification

### Command Used

- show vlan brief

### Result
- VLANs were successfully created on both switches
- Access ports were assigned to the correct VLANs
- Devices appeared under the correct VLAN assignments

---

## Trunk Verification

### Command Used

- show interface trunk

### Result
- Trunk link between switches is active
- Correct encapsulation (802.1Q) is in use
- Required VLANs are allowed across the trunk
- Native VLAN is consistent across both switches

---

## Interface Verification

### Command Used

- show interfaces status

### Result
- All relevant interfaces are up/up
- Access ports are assigned correctly
- Trunk port is operational

---

## Connectivity Testing

### Method
Ping tests were performed between devices in:

- Same VLAN (expected: success)
- Different VLANs without routing (expected: failure)

### Result
- Devices within the same VLAN successfully communicated
- Devices in different VLANs could not communicate (expected behavior without Layer 3 routing)

---

## Overall Result

The VLAN segmentation and trunk configuration were successfully implemented.

- VLAN isolation is functioning as expected
- Trunk link is correctly passing tagged traffic
- Network behavior aligns with design expectations

This confirms that the lab objectives were fully achieved.