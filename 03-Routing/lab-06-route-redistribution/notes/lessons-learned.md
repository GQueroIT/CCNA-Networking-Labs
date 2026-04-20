# Lessons Learned

This lab helped reinforce that route redistribution is not just about configuring another routing protocol. The real objective was understanding how a router can act as a boundary between two different routing domains and allow them to exchange reachability information in a controlled way.

One of the most important things I learned was that each router only advertises its own directly connected networks into the routing protocol running on that router. I had to stay disciplined about not trying to manually add remote networks into OSPF or EIGRP where they did not belong. Once I kept that idea clear in my head, the lab made much more sense.

I also learned that redistribution is where the real logic of the lab begins. Before redistribution was configured, the OSPF side and the EIGRP side were both functioning correctly on their own, but they had no knowledge of each other’s internal networks. That failure point was expected and actually helped me verify that the lab was behaving correctly before the final step was applied.

Another strong takeaway from this lab was the importance of metrics during redistribution. EIGRP requires a metric when external routes are injected into the protocol. Without that, the redistribution process will not work properly. OSPF also required the `subnets` keyword so that the redistributed EIGRP routes would be carried correctly.

Using a loopback interface on R2 was also useful because it allowed me to simulate an additional LAN without cluttering the topology with another endpoint. That made the routing table more interesting and gave me another network to verify after redistribution.

This lab pushed me beyond basic single-protocol routing and helped me understand how enterprise networks may need to connect multiple routing environments together while still maintaining full reachability.