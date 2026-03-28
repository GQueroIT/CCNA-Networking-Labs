# Troubleshooting

## Issue Observed

During early simulation testing, communication between devices did not fully complete.

---

## Initial Analysis

Basic connectivity appeared to be correct. However, when switching to Simulation Mode, issues were observed during ARP resolution and TCP session establishment.

---

## Troubleshooting Process

The following steps were taken to identify and resolve the issue:

- Verified IP addressing on all devices
- Confirmed both PCs were in the same subnet
- Checked server configuration
- Enabled HTTP service
- Used ping to confirm basic connectivity
- Observed packet flow in Simulation Mode, including:
  - ARP request and reply
  - TCP three-way handshake (SYN, SYN-ACK, ACK)
  - HTTP request and response

---

## Resolution

After verifying configurations and observing protocol behavior step-by-step, communication between devices completed successfully.

---

## Key Insight

Simulation Mode provides visibility into how protocols operate under the hood, not just whether connectivity works.

Understanding packet flow is critical for diagnosing issues in real-world networking environments.