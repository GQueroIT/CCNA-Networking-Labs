# Lessons Learned

## Key Takeaways

- VLANs create separate broadcast domains even when devices are connected through the same switching environment.
- Trunk links are required to carry traffic for multiple VLANs between network devices.
- Inter-VLAN communication does not happen by default and requires a Layer 3 device.
- In a router-on-a-stick design, each VLAN needs its own router subinterface and gateway IP address.
- When a ping fails, I need to determine whether the problem is Layer 2 or Layer 3 before making changes.
- ARP failures usually point me toward a local VLAN, switching, or MAC resolution issue before routing is even involved.

## What This Lab Reinforced For Me

This lab made the packet flow more real for me. It helped me understand that same-VLAN communication depends on proper Layer 2 switching, while different VLAN communication depends on both working Layer 2 paths and correct Layer 3 gateway configuration. It also reinforced that small mistakes, like choosing the wrong router interface type, can stop the whole design from working.