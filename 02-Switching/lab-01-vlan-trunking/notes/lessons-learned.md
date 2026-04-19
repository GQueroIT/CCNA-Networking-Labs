# Lessons Learned

This lab helped me understand how VLANs actually behave in a real network instead of just reading about them conceptually.

One of the biggest takeaways for me was seeing how VLANs separate broadcast domains at Layer 2. Even though devices are physically connected to the same switch, they cannot communicate unless they are in the same VLAN. That made the concept of segmentation much clearer.

I also learned how important trunk links are when working with multiple switches. Without a properly configured trunk, VLAN traffic does not pass between switches, which completely breaks communication across the network. Verifying the trunk with `show interfaces trunk` became one of the first things I checked when something was not working.

Another thing that stood out to me was how easy it is to misconfigure access ports. Assigning a port to the wrong VLAN immediately causes connectivity issues, even if everything else is configured correctly. Using `show vlan brief` helped me quickly confirm whether ports were assigned properly.

This lab also reinforced the importance of verification commands. Instead of guessing what might be wrong, I used commands like `show vlan brief`, `show interfaces trunk`, and basic ping testing to confirm exactly where the problem was.

Overall, this lab helped me move from just configuring commands to actually understanding how VLANs and trunking behave in a working network.