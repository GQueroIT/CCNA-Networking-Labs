During this lab, I gained a deeper understanding of how EtherChannel operates and how it improves both redundancy and bandwidth within a switched network. Instead of relying on a single physical link, EtherChannel allows multiple interfaces to be bundled together into a single logical interface, which is seen by spanning-tree as one link. This prevents unnecessary blocking while still maintaining loop prevention.

One of the most important concepts I reinforced was the difference between static EtherChannel and LACP (Link Aggregation Control Protocol). By configuring LACP with active and passive modes, I observed how negotiation occurs dynamically between switches, making the configuration more flexible and reliable compared to static configurations.

I also learned that consistency is critical when configuring EtherChannel. All interfaces participating in the channel group must have identical settings, including speed, duplex, VLAN assignments, and trunking configuration. Any mismatch will cause the EtherChannel to fail or not form correctly.

Another key takeaway was how EtherChannel interacts with trunking. The Port-Channel interface itself carries the trunk configuration, not the individual physical interfaces once they are bundled. This reinforced the concept that the logical interface is what ultimately handles traffic forwarding.

This lab helped solidify my understanding of link aggregation, redundancy, and how enterprise networks optimize performance while maintaining stability.