## Troubleshooting

During the configuration and validation of OSPF in this lab, I focused on verifying proper neighbor adjacency and route propagation across all routers. While the overall setup worked as expected, I paid close attention to common issues that can prevent OSPF from forming correctly.

One of the first things I verified was that all participating interfaces were enabled and correctly addressed. If an interface is shut down or assigned an incorrect IP address, OSPF will not establish a neighbor relationship. Ensuring that all interfaces were in an up/up state was critical before moving forward with protocol verification.

I also validated that all routers were configured within the same OSPF area. Since this lab uses a single-area design (Area 0), any mismatch in area configuration would prevent adjacency from forming. This is one of the most common issues when working with OSPF and something I made sure to double-check during setup.

Another potential issue I considered was incorrect wildcard masks in the network statements. Using an incorrect wildcard mask can prevent OSPF from enabling on the intended interfaces, which would stop routes from being advertised. Verifying that /24 networks used 0.0.0.255 and /30 networks used 0.0.0.3 ensured proper participation in OSPF.

I used verification commands such as `show ip ospf neighbor` to confirm that routers reached a FULL adjacency state, and `show ip route` to ensure that remote networks were being learned dynamically with the "O" designation. These commands were essential in confirming that OSPF was functioning properly across the topology.

Finally, I ensured that any previously configured static routes were removed so they would not take precedence over OSPF-learned routes. Since static routes have a lower administrative distance, leaving them in place could mask whether OSPF was actually working.

Overall, the troubleshooting process reinforced the importance of validating interface status, correct network statements, and proper protocol behavior using show commands.