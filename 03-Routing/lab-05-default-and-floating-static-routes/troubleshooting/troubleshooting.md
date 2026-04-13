# Troubleshooting

During the implementation of this lab, several issues were encountered that helped reinforce a deeper understanding of routing behavior and network design.

The first issue observed was intermittent packet loss when testing connectivity between PC1 and PC2. Initial pings would either fail completely or return partial success. This behavior indicated that the network was not consistently forwarding traffic along a stable path. After investigation, the root cause was identified as asymmetric routing. Traffic was taking one path in the forward direction and a different path on the return, which resulted in inconsistent communication. This was resolved by ensuring that both R1 and R4 had matching primary and floating static route configurations so that forward and return traffic followed the same path.

Another issue involved the floating static route not appearing in the routing table. At first, it seemed like the configuration was incorrect, but further analysis showed that the route was functioning as expected. The floating route does not install in the routing table unless the primary route is removed. This was verified by shutting down the primary link between R1 and R2, which caused the floating route to immediately take over and appear in the routing table.

A configuration mistake was also identified on R4, where both static routes initially pointed to the same next-hop address. This prevented proper failover behavior and caused inconsistent return paths. The issue was corrected by assigning the primary route to the R2 path and the floating route to the R3 path with a higher administrative distance. Once corrected, failover behavior became consistent and predictable.

During failover testing, a brief period of packet loss was observed immediately after shutting down the primary link. This was expected behavior and was caused by the time required for the router to remove the primary route and install the floating route. After this short convergence period, connectivity stabilized and traffic successfully flowed through the backup path.

These troubleshooting steps reinforced the importance of verifying routing tables, understanding route selection logic, and ensuring that both forward and return paths are properly aligned in a network design.