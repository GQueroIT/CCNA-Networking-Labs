## Lessons Learned

This lab reinforced my understanding of how Spanning Tree Protocol (STP) operates to prevent switching loops within a Layer 2 network. Prior to this, I understood the concept of loops at a high level, but this exercise allowed me to actually observe how STP dynamically controls traffic flow by placing certain ports into a blocking state.

One of the most important takeaways was how the root bridge influences the entire topology. By manually adjusting the bridge priority on one of the switches, I was able to control which switch became the root bridge. This directly affected how all other switches selected their root ports and forwarding paths. Seeing this behavior in real time made it clear how critical root bridge placement is in a production environment.

I also explored path cost manipulation and how it can be used to influence port roles and traffic flow. By increasing the cost on a specific interface, I was able to force STP to choose an alternate path, which resulted in a different port being placed into a blocking state. This demonstrated how network engineers can fine-tune Layer 2 behavior without physically changing the topology.

Another key observation was how STP automatically recalculates the topology when changes occur. When links were disconnected or costs were adjusted, the switches reconverged and selected new optimal paths. This highlighted the importance of convergence time and stability in network design.

Overall, this lab helped bridge the gap between theory and practical implementation. Instead of just memorizing STP concepts, I was able to validate how root bridges, root ports, designated ports, and blocked ports interact in a real environment. This is a foundational concept that will carry over into more advanced switching and network design topics.