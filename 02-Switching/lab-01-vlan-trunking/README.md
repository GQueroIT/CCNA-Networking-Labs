# Lab 01 — VLAN Trunking (Switching)


## Objective

In this lab, I configured VLAN segmentation across two switches and implemented trunking to allow communication between devices in the same VLAN across different switches. The goal was to understand how VLANs isolate traffic and how trunk links carry multiple VLANs between switches.

---

## Topology

- 2 Switches (S1, S2)
- 4 PCs (PC1, PC2, PC3, PC4)

PC1 and PC2 are connected to S1.  
PC3 and PC4 are connected to S2.  
S1 and S2 are connected via a trunk link.

---

## VLAN Configuration

| VLAN | Name  | Devices        |
|------|------|----------------|
| 10   | SALES | PC1, PC3       |
| 20   | HR    | PC2            |
| 30   | IT    | PC4            |

---

## Key Configurations

- Created VLANs on both switches
- Assigned access ports to the correct VLANs
- Configured trunk link between S1 and S2
- Verified trunk operation using `show interfaces trunk`

---

## Evidence

Screenshots are located in the `/evidence` folder and include:

- VLAN configuration on both switches
- Trunk status verification
- Successful and failed ping tests

---

## Key Takeaways

- VLANs segment network traffic at Layer 2
- Trunk links allow multiple VLANs to traverse between switches
- Devices in different VLANs cannot communicate without Layer 3 routing
- Consistent VLAN configuration across switches is critical for proper operation

---

## Troubleshooting

- CLI commands needed to configure switchports
- Mislabeling of devices caused confusion during verification
- Ensured VLANs existed on both switches to maintain consistency across the trunk