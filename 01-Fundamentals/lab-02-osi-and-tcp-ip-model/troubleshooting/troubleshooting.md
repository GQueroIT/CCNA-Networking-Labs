\# Troubleshooting



\## Issue Observed



Initial communication between devices did not fully complete during early simulation testing.



---



\## Analysis



Basic connectivity seemed fine, but when I switched to Simulation Mode, I noticed issues during ARP resolution and TCP session setup.



---



\## Steps Taken



\- Verified IP addressing on all devices  

\- Confirmed both PCs were in the same subnet  

\- Checked server configuration  

\- Enabled HTTP service  

\- Used ping to confirm connectivity  

\- Observed packet flow in Simulation Mode:

&nbsp; - ARP request and reply  

&nbsp; - TCP handshake (SYN, SYN-ACK, ACK)  

&nbsp; - HTTP request and response  



---



\## Resolution



After correcting the configuration and verifying each step, communication completed successfully.



---



\## Takeaway



Simulation Mode makes a big difference. It shows what’s actually happening, not just whether something works.

