# Concepts

## OSI Model

The OSI (Open Systems Interconnection) model is a conceptual framework used to understand how data travels across a network. Each layer has a specific role in the communication process.

### Layer 1 — Physical
The physical layer is responsible for transmitting raw bits across the medium. This includes cabling, electrical signals, and physical connections.

### Layer 2 — Data Link
The data link layer handles MAC addressing and frame delivery. This is where ARP operates to resolve IP addresses to MAC addresses. Switches function at this layer.

### Layer 3 — Network
The network layer is responsible for IP addressing and routing. Protocols like ICMP operate here to test connectivity between devices.

### Layer 4 — Transport
The transport layer ensures reliable communication between devices. TCP provides connection-oriented communication, while UDP provides faster, connectionless communication.

### Layer 7 — Application
The application layer is where user interaction occurs. Protocols such as HTTP operate here to allow communication between client and server.

---

## TCP/IP Model

The TCP/IP model simplifies networking into four layers and maps directly to the OSI model.

- Application Layer → OSI Layers 5–7
- Transport Layer → OSI Layer 4
- Internet Layer → OSI Layer 3
- Network Access Layer → OSI Layers 1–2

---

## ARP (Address Resolution Protocol)

ARP is used to resolve an IP address to a MAC address before communication can begin. It sends a broadcast request and receives a unicast reply.

---

## ICMP (Ping)

ICMP is used to test connectivity between devices. It operates at the network layer and does not use port numbers.

---

## TCP (Transmission Control Protocol)

TCP is a connection-oriented protocol that ensures reliable data delivery. It uses a three-way handshake to establish communication:

- SYN
- SYN-ACK
- ACK

---

## HTTP (Hypertext Transfer Protocol)

HTTP operates at the application layer and uses TCP (port 80) to send and receive web data through a request and response model.

---

## Packet Flow Observations

During this lab, I observed the following sequence:

1. ARP request is sent to resolve the destination MAC address
2. ARP reply is received
3. ICMP is used to verify connectivity
4. TCP handshake establishes a connection
5. HTTP request and response completes communication

---

## Key Takeaways

This lab reinforced the importance of understanding how each layer of the OSI and TCP/IP models interacts. Observing traffic in simulation mode made it clear how protocols depend on one another to complete communication.