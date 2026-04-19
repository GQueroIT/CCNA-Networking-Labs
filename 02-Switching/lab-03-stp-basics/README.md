# Lab 03 - Spanning Tree Protocol (STP) Basics

## Objective

The goal of this lab was to understand how Spanning Tree Protocol (STP) prevents Layer 2 switching loops and how port roles are dynamically assigned within a redundant network topology.

This lab focused on:
- Root Bridge election
- Port roles (Root, Designated, Blocking)
- STP reconvergence
- Manual manipulation of STP using priority and cost

---

## Technologies Used

- Cisco Packet Tracer
- Cisco Catalyst 2960 Switches
- Spanning Tree Protocol (IEEE 802.1D)

---

## Topology

3-switch triangle topology was used to intentionally create a Layer 2 loop.

- SW1
- SW2
- SW3
- 2 End Devices (PC1, PC2)

Redundant links were configured between all switches to allow STP to determine the optimal path.

---

## STP Behavior Observed

### Initial State

- SW1 became the Root Bridge (lowest MAC address)
- All ports on SW1 were in forwarding state
- One port on SW3 entered blocking state to prevent loops

### After Root Bridge Manipulation

SW2 was manually configured as the Root Bridge:

```
spanning-tree vlan 1 priority 24576
```

- STP reconverged across the topology
- Root ports recalculated on all switches
- Blocking port location changed

### After Cost Manipulation

On SW3, interface cost was increased:

```
interface fa0/4
spanning-tree cost 50
```

- STP selected a different Root Port
- Blocking port shifted from one interface to another
- Demonstrated path selection based on cost

---

## Verification Commands

```
show spanning-tree
show running-config
```

---

## Key Concepts Learned

- STP operates at Layer 2 to prevent switching loops
- Root Bridge is selected based on lowest Bridge ID (priority + MAC)
- Root Ports are the best path toward the Root Bridge
- Designated Ports forward traffic for each segment
- Blocking ports prevent loops without removing physical connections
- STP dynamically recalculates topology when changes occur
- Path cost directly influences STP decisions

---

## Notes

This lab demonstrated how STP not only prevents loops but also provides redundancy by maintaining backup paths that can become active if needed.

Understanding STP behavior is critical for troubleshooting switching issues and designing resilient Layer 2 networks.

---

## Files

- Topology file located in `/topology`
- Device configurations located in `/configs`
- Evidence screenshots located in `/evidence`
- Additional notes located in `/notes`
- Troubleshooting documentation located in `/troubleshooting`