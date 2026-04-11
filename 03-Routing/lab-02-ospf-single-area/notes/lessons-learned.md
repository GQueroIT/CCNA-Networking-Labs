## Lessons Learned

In this lab, I focused on implementing OSPF as a dynamic routing protocol within a single-area network design. One of the most important takeaways for me was understanding how OSPF forms neighbor adjacencies automatically once interfaces are correctly configured and placed within the same area. Seeing the routers reach a FULL state confirmed that communication between devices was successfully established without the need for manual routing entries.

Another key concept I reinforced was the use of wildcard masks in OSPF network statements. Unlike subnet masks, wildcard masks define which portions of the IP address should be matched, and getting comfortable with this translation was essential for proper OSPF configuration.

I also gained a deeper understanding of how routing tables change when transitioning from static routing to dynamic routing. After removing static routes, I was able to observe OSPF-learned routes appearing with the "O" designation, which confirmed that the routers were exchanging routing information dynamically.

Additionally, I learned the importance of verification commands such as `show ip ospf neighbor`, `show ip route`, and `show ip protocols`. These commands allowed me to validate adjacency, confirm route propagation, and ensure that OSPF was operating as expected across the network.

This lab helped me solidify my understanding of how OSPF simplifies network scalability and reduces administrative overhead compared to static routing, while also reinforcing the importance of proper verification and structured configuration.