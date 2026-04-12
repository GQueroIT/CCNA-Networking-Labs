# Troubleshooting

During this lab, I encountered several issues that required me to slow down and verify each layer of the network instead of assuming the configuration was correct.

One of the first issues I ran into was end devices not being able to communicate across the network even though router-to-router connectivity appeared to be working. I was able to ping between routers, but not from PCs to remote networks. This forced me to step back and verify the switching side of the network instead of focusing only on routing.

I started by checking VLAN assignments using `show vlan brief` on the switches. This allowed me to confirm that the correct ports were placed into the appropriate VLANs. After that, I verified trunking between switches and routers using `show interfaces trunk`. This helped confirm that VLANs 10 and 20 were actually being carried across the trunk links.

Another issue I worked through involved router-on-a-stick configuration. I verified that subinterfaces were correctly configured with the proper VLAN encapsulation using the `encapsulation dot1Q` command and that each subinterface had the correct IP address acting as the default gateway for its VLAN. I also confirmed that the physical interface was enabled, since forgetting `no shutdown` can silently break connectivity.

When validating routing, I used `show ip ospf neighbor` to confirm that adjacencies were forming correctly between routers. This was important because if OSPF neighbors do not reach a FULL state, routes will not be exchanged. I also used `show ip protocols` to verify that the correct networks were being advertised into OSPF and placed in the proper areas.

To confirm that routing was working end-to-end, I used `show ip route` to check whether remote networks were being learned dynamically. If a network was missing from the routing table, it pointed directly to an issue in OSPF configuration or network statements.

Throughout the troubleshooting process, I relied heavily on `show ip interface brief` to quickly verify interface status and IP addressing. This helped me identify whether interfaces were up or down and whether they had the correct configurations applied.

The biggest lesson from troubleshooting this lab was the importance of following a structured process. Instead of guessing, I moved step by step through switching, trunking, interface configuration, and routing. This approach made it much easier to isolate issues and fix them efficiently.