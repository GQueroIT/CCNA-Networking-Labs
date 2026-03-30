# Lessons Learned

- VLANs create separate Layer 2 broadcast domains even when devices are connected through the same switching environment.
- Trunk ports are required to carry traffic for multiple VLANs between switches.
- Access ports must be assigned to the correct VLAN or host communication will fail.
- Verification matters just as much as configuration. `show vlan brief` and `show interfaces trunk` were critical in confirming correct behavior.
- A mislabeled screenshot or device can create confusion during validation, even when the configuration is correct.
- This lab reinforced the difference between simple Layer 2 segmentation and future Layer 3 inter-VLAN routing concepts.