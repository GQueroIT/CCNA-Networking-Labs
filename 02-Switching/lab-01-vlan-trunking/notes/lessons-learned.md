# Lessons Learned

In this lab, I learned how VLANs are used to segment a network at Layer 2 and how that segmentation directly impacts communication between devices.

One of the biggest takeaways for me was understanding that devices in the same VLAN can communicate even when they are on different switches, as long as a trunk link is properly configured. Seeing PC1 successfully communicate with PC3 across the trunk helped reinforce how VLAN traffic is carried between switches.

I also saw firsthand how VLANs isolate traffic. Devices in different VLANs were unable to communicate, which made it clear that VLANs act as separate broadcast domains. This helped me better understand why inter-VLAN routing is required for communication between VLANs.

Another important lesson was the need for consistency across switches. VLANs must exist on both switches for proper operation across a trunk. Missing a VLAN can lead to connectivity issues that are not immediately obvious.

I also learned that proper labeling and documentation matter. At one point, I mislabeled a device, which caused confusion during testing. Fixing that showed me how important clear documentation is during troubleshooting.

Overall, this lab strengthened my understanding of Layer 2 switching, VLAN behavior, and trunking, and it prepared me for the next step, which is inter-VLAN routing.