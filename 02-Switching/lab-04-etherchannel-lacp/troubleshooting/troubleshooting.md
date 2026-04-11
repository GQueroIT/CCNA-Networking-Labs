# Troubleshooting Steps

During this lab, several potential issues were identified and validated to ensure proper EtherChannel functionality.

One of the primary checks involved verifying that all interfaces participating in the EtherChannel were configured consistently. EtherChannel requires matching configurations across all member interfaces, including trunking mode, VLAN settings, and speed/duplex. Any mismatch would prevent the channel from forming correctly.

Another important validation step was confirming the LACP configuration. On SW1, interfaces were configured using "channel-group 1 mode active," while SW2 used "channel-group 1 mode passive." This ensured proper LACP negotiation, as at least one side must be in active mode for the EtherChannel to establish successfully.

Verification commands such as "show etherchannel summary" were used to confirm that the Port-Channel was in an operational state and that all member interfaces were bundled correctly. Additionally, "show interfaces trunk" was used to confirm that VLAN traffic was properly traversing the trunk link.

Spanning Tree Protocol behavior was also considered. Since EtherChannel presents itself as a single logical interface, it prevents STP from blocking individual links, which improves both efficiency and redundancy.

If issues were encountered, the following corrective actions would be taken:
- Reconfigure mismatched interfaces
- Remove and re-add interfaces to the channel group
- Verify trunk configuration on the Port-Channel interface
- Ensure LACP modes are correctly assigned

These steps ensure a stable and properly functioning EtherChannel deployment.