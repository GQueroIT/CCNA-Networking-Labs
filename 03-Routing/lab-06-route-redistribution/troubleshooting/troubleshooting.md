# Troubleshooting

## Issue
PC1 could successfully reach its local default gateway, R2, and R3, but it could not reach the remote endpoint on the R4 side of the topology.

## Symptoms Observed
- Local gateway connectivity was successful
- OSPF-side transit connectivity was successful
- Ping to the remote EIGRP-side endpoint failed
- The error returned indicated that the source-side router did not have a route to the remote destination network

## Root Cause
At that stage of the lab, OSPF and EIGRP were functioning as separate routing domains. Even though both sides were individually configured correctly, no route redistribution had been configured yet on R3. Because of that, the OSPF domain had no knowledge of the 192.168.40.0/24 network, and the EIGRP domain had no knowledge of the OSPF-learned networks.

## Corrective Actions
I first confirmed that the OSPF side of the topology was operating correctly by testing hop-by-hop connectivity from PC1 toward R3. After that, I verified that the EIGRP side was configured correctly on R4 and that adjacency between R3 and R4 could form properly.

Once both routing domains were independently validated, I configured route redistribution on R3 in both directions:
- OSPF into EIGRP with an explicit metric
- EIGRP into OSPF using the `subnets` keyword

## Verification Performed
After redistribution was configured, I verified the following:
- R1 could learn the remote 192.168.40.0/24 network
- R4 could learn the OSPF-side networks
- End-to-end ping from PC1 to the remote endpoint succeeded
- The routing table reflected external route learning across the redistribution boundary

## Key Troubleshooting Takeaway
The most important troubleshooting lesson from this lab was that successful local or partial connectivity does not always mean end-to-end routing is complete. In this case, the routers were working correctly within their own protocols, but reachability failed at the protocol boundary until redistribution was configured.