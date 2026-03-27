\# Lab 02 — OSI \& TCP/IP Model Analysis (Packet Tracer)



\## 📌 Objective

In this lab, I analyzed how data flows through both the OSI and TCP/IP models by generating network traffic and observing packet behavior using Cisco Packet Tracer simulation mode.



The goal was to build a deeper understanding of encapsulation, protocol interaction, and how different layers operate together during communication.



---



\## 🧰 Technologies Used

\- Cisco Packet Tracer

\- ICMP (Ping)

\- ARP

\- TCP

\- HTTP



---



\## 🖥️ Topology

\- 2 PCs

\- 1 Switch (Cisco 2960)

\- 1 Server (HTTP enabled)



Topology file located in `/topology`



---



\## 🌐 IP Addressing



| Device | IP Address | Subnet Mask |

|--------|-----------|------------|

| PC0 | 192.168.1.10 | 255.255.255.0 |

| PC1 | 192.168.1.20 | 255.255.255.0 |

| Server | 192.168.1.30 | 255.255.255.0 |



---



\## 🔍 Key Concepts Demonstrated



\### ARP (Address Resolution Protocol)

Observed how a device resolves an IP address to a MAC address before communication begins.



---



\### ICMP (Ping)

Validated connectivity and observed packet flow between devices.



---



\### TCP (Transmission Control Protocol)

Analyzed the 3-way handshake process:

\- SYN

\- SYN-ACK

\- ACK



---



\### HTTP (Hypertext Transfer Protocol)

Captured request/response communication between client and server.



---



\## 📦 Encapsulation Process

Traffic was observed moving through layers:

Application → Transport → Network → Data Link → Physical



---



\## 🔄 De-encapsulation

Incoming traffic was processed in reverse order at the destination device.



---



\## 📸 Evidence

All screenshots and packet analysis are located in `/evidence`, including:

\- ARP request/response

\- ICMP packet flow

\- TCP handshake

\- HTTP communication



---



\## 🛠️ Troubleshooting

Basic connectivity validation was performed using ping and simulation mode analysis.



---



\## 🧠 Key Takeaways

\- ARP operates at Layer 2 but enables Layer 3 communication

\- TCP ensures reliable delivery through session establishment

\- Understanding packet flow is critical for troubleshooting and exams

\- Simulation mode provides visibility into real network behavior



---



\## 📁 Author

Gabriel Quero  

Aspiring Network Engineer | CCNA Candidate

