# Lessons Learned

This lab reinforced how critical accuracy is when working with static routing. Unlike dynamic routing protocols, static routes must be manually configured, which means any incorrect destination network or next-hop IP immediately breaks connectivity. Even a small mistake in a single route can prevent communication across the entire topology.

One key takeaway was understanding how routers rely entirely on their routing tables to make forwarding decisions. Verifying routes using `show ip route` proved essential in confirming whether the correct paths were installed and identifying where traffic was being dropped.

Another important observation was the behavior of ARP (Address Resolution Protocol) during initial connectivity testing. The first ping attempt may fail because the device has not yet resolved the MAC address of the next-hop router. Once the ARP table is populated, subsequent pings succeed. This highlighted the interaction between Layer 2 and Layer 3 and reinforced the importance of not immediately assuming a configuration issue when the first test fails.

Additionally, this lab emphasized the importance of a structured troubleshooting approach. Breaking the network down step-by-step—verifying interfaces, checking IP addressing, confirming routing tables, and testing connectivity incrementally—made it easier to isolate and resolve issues efficiently.

Overall, this lab strengthened my understanding of how static routing operates, how routing tables influence traffic flow, and how to troubleshoot routing issues in a methodical and effective way.