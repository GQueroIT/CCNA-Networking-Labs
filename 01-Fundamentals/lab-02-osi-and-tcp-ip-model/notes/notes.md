\# Lab 02 Notes — OSI \& TCP/IP Model



\## OSI Layers (What Happens Where)



Layer 1 — Physical  

\- Sends raw bits over cable  



Layer 2 — Data Link  

\- MAC addressing  

\- ARP happens here  

\- Switches operate here  



Layer 3 — Network  

\- IP addressing  

\- Routing  

\- ICMP (ping)  



Layer 4 — Transport  

\- TCP/UDP  

\- Ports  

\- Reliability  



Layer 7 — Application  

\- HTTP  

\- User interaction  



---



\## TCP/IP Model Mapping



Application → OSI 5–7  

Transport → OSI 4  

Internet → OSI 3  

Network Access → OSI 1–2  



---



\## Key Protocol Behavior



ARP  

\- Finds MAC address from IP  

\- Broadcast request  

\- Unicast reply  



ICMP  

\- Used for ping  

\- Tests connectivity  

\- No ports  



TCP  

\- Connection-oriented  

\- Reliable  

\- Uses 3-way handshake  



HTTP  

\- Runs on TCP  

\- Uses port 80  

\- Request/response  



---



\## Packet Flow (What I Observed)



1\. ARP request happens first  

2\. MAC address gets learned  

3\. ICMP ping is sent  

4\. TCP handshake begins (for HTTP)  

5\. HTTP request/response occurs  



---



\## Key Takeaways



\- Communication cannot happen without ARP first  

\- TCP must establish a connection before sending data  

\- Simulation mode shows real packet behavior  

\- Each layer has a specific responsibility

