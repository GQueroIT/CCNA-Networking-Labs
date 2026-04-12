## Lessons Learned

In this lab, I implemented inter-VLAN routing using a router-on-a-stick design. This reinforced my understanding of how VLANs separate broadcast domains at Layer 2, and how a router is required to enable communication between those VLANs at Layer 3.

I configured multiple VLANs on a switch and assigned access ports to each VLAN. I then configured a trunk link between the switch and the router, allowing multiple VLANs to traverse a single physical connection using IEEE 802.1Q tagging. This demonstrated how VLAN traffic is encapsulated and transported across trunk links.

On the router, I configured subinterfaces on a single physical interface. Each subinterface was assigned to a specific VLAN using encapsulation dot1Q, along with an IP address that served as the default gateway for that VLAN. This showed how a single router interface can logically act as multiple gateways.

One important observation during testing was that the first ping attempt between devices in different VLANs sometimes failed. This was due to ARP resolution, where the device needed to learn the MAC address of the destination before successful communication could occur. Once ARP was completed, subsequent pings succeeded without issue.

This lab helped solidify the relationship between switching and routing, and how both are required to properly segment and connect networks in a real-world environment.