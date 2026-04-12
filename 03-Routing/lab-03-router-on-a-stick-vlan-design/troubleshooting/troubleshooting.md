## Troubleshooting

During this lab, I validated connectivity across all VLANs and ensured that inter-VLAN routing was functioning properly. One initial observation was that the first ping attempt between devices in different VLANs sometimes resulted in a timeout. This behavior was expected and was caused by ARP resolution, where the device must first learn the MAC address of the destination before communication can be established.

To verify correct operation, I checked VLAN assignments on the switch using the `show vlan brief` command and confirmed that each access port was assigned to the correct VLAN. I also verified the trunk configuration using `show interfaces trunk` to ensure that all VLANs were being allowed across the trunk link.

On the router, I used `show ip interface brief` and `show running-config` to confirm that all subinterfaces were properly configured with the correct encapsulation and IP addressing. I also ensured that the physical interface connected to the switch was not administratively down.

End-to-end connectivity was tested using ping commands between all hosts across different VLANs. After confirming that all devices could successfully communicate, I determined that the configuration was correct and the network was functioning as expected.