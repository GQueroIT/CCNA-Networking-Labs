# Lab 02 — OSI & TCP/IP Model Analysis (Packet Tracer)

## Objective
In this lab, I analyzed how data flows through both the OSI and TCP/IP models by generating network traffic and observing packet behavior using Cisco Packet Tracer simulation mode.

The goal was to build a deeper understanding of encapsulation, protocol interaction, and how different layers operate together during communication.

---

## Technologies Used
- Cisco Packet Tracer
- ICMP (Ping)
- ARP
- TCP
- HTTP

---

## Topology
- 2 PCs
- 1 Switch (Cisco 2960)
- 1 Server (HTTP enabled)

Topology file located in `/topology`.

---

## IP Addressing

| Device | IP Address | Subnet Mask |
|--------|-----------|------------|
| PC0    | 192.168.1.10 | 255.255.255.0 |
| PC1    | 192.168.1.20 | 255.255.255.0 |
| Server | 192.168.1.30 | 255.255.255.0 |

---

## Key Concepts Demonstrated

### ARP (Address Resolution Protocol)
Observed how a device resolves an IP address to a MAC address before communication begins.

### ICMP (Ping)
Validated connectivity and observed packet flow between devices.

### TCP (Transmission Control Protocol)
Analyzed the three-way handshake process:
- SYN
- SYN-ACK
- ACK

### HTTP (Hypertext Transfer Protocol)
Captured request and response communication between client and server.

---

## Encapsulation Process
Traffic was observed moving through the following layers:

Application → Transport → Network → Data Link → Physical

---

## De-encapsulation
Incoming traffic was processed in reverse order at the destination device.

---

## Evidence
All screenshots and packet analysis are located in `/evidence`, including:
- ARP request and response
- ICMP packet flow
- TCP handshake
- HTTP communication

---

## Troubleshooting
Basic connectivity validation was performed using ping and simulation mode analysis. Additional troubleshooting notes are documented in `/troubleshooting/troubleshooting.md`.

---

## Key Observations
- ARP operates at Layer 2 to resolve MAC addresses before communication begins
- TCP establishes reliable communication using a three-way handshake
- HTTP operates at the Application Layer and depends on lower-layer protocols
- Packet Tracer Simulation Mode provides visibility into encapsulation and protocol flow

---

## Skills Demonstrated
- OSI model understanding
- TCP/IP model mapping
- Packet-level analysis
- Protocol interaction (ARP, TCP, HTTP)
- Network troubleshooting using simulation tools

---

## Author
Gabriel Quero  
Aspiring Network Engineer | CCNA Candidate