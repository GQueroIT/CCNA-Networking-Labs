\# Troubleshooting



\## Issue Observed



Initial communication between devices did not fully complete during early simulation testing.



\## Analysis



While basic connectivity appeared functional, deeper inspection using Packet Tracer Simulation Mode revealed incomplete protocol interactions, particularly during ARP resolution and TCP session establishment.



\## Steps Taken



\- Verified IP addressing on all devices

\- Confirmed both PCs were within the same subnet

\- Checked server configuration

\- Enabled HTTP service on the server

\- Used ICMP (ping) to confirm Layer 3 connectivity

\- Observed packet flow in Simulation Mode:

&nbsp; - ARP request and reply

&nbsp; - TCP three-way handshake (SYN, SYN-ACK, ACK)

&nbsp; - HTTP request and response



\## Resolution



After validating device configurations and confirming proper protocol sequencing, full communication was successfully established between devices.



\## Key Takeaway



Simulation Mode is critical for understanding how protocols interact across layers, especially when troubleshooting connectivity beyond simple ping tests.

