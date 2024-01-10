---
title: Basics of networking
date: 2023-11-07
resources: 
tags:
  - networking
---
# Table of contents

- [[#Purpose of Networking|Purpose of Networking]]
- [[#Layer 1 - Physical layer (Transporting Bits)|Layer 1 - Physical layer (Transporting Bits)]]
- [[#Layer 2 - Data Link (Hop to Hop delivery)|Layer 2 - Data Link (Hop to Hop delivery)]]
- [[#Layer 3 - Network Layer (end to end delivery)|Layer 3 - Network Layer (end to end delivery)]]
	- [[#Layer 3 - Network Layer (end to end delivery)#Layer 2 MAC Address vs Layer 3 IP addresses|Layer 2 MAC Address vs Layer 3 IP addresses]]
- [[#Layer 4 - Transport Layer (Service to Service delivery)|Layer 4 - Transport Layer (Service to Service delivery)]]
- [[#Layer 5, 6, 7 - Session, Presentation, Application|Layer 5, 6, 7 - Session, Presentation, Application]]
- [[#Data flow through all the layers|Data flow through all the layers]]

---
# Purpose of Networking

Allow two hosts to share data with one another.

- Hosts must follow a set of rules
- The rules for networking are divided into 7 layers:‘
	- OSI model
	- ![[Pasted image 20231107165228.png | 200]]
	- if all these layers are functioning, hosts can share data

---

# Layer 1 - Physical layer (Transporting Bits)

- Computer data exists in the form of bits.
- Something has to transport those bits between hosts
- L1 Technologies: 
	1. **Cables**
	2. **Wifi**
	3. **Repeaters**
	4. **Hubs**

---

# Layer 2 - Data Link (Hop to Hop delivery)

- Interacts with Wire (i.e., Physical layer)
	- **NIC** - Network Interface Cards / Wifi Access Cards.
- <mark style="background: #BBFABBA6;">Addressing Scheme - MAC addresses</mark>
	- 48 bits, represented as 12 hex digits
	- 94-65-9C-3B-8A-E5 / 94:65:9C:3B:8A:E5 / 9465.9C3B.8AE5
	- Every NIC has a unique MAC address.
- Often communication between hosts require multiple hops.
- L2 Technologies: **NICs**, **Switches**

---

- ! If Layer 2 Layer is taking care of every hop. what ensures of data from one end point to another endpoint.

# Layer 3 - Network Layer (end to end delivery)

- <mark style="background: #BBFABBA6;">Addressing Scheme - IP addresses</mark>
	- 32 bits, represented as 4 octets, each 0-255
- L3 Technologies: **Routers**, **Hosts**, (**anything with an IP**)

## Layer 2 MAC Address vs Layer 3 IP addresses

<iframe width="560" height="315" src="https://www.youtube.com/embed/LkolbURrtTs?si=nyI9ksArK2eZUiZW&amp;start=512" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

- ! There is a protocol which ties or links the two layers (2 and 3) called **ARP Address Resolution Protocol**.

---

![[Pasted image 20231107174832.png | 500]]

---
# Layer 4 - Transport Layer (Service to Service delivery)


- ! How do we make sure that right programs receives the right packets.
- Distinguish data streams
- <mark style="background: #BBFABBA6;">Addressing Scheme - ports</mark>
- **TCP** and **UDP** are 2 different strategies to distinguish data streames.

| TCP             | UDP            |
| --------------- | -------------- |
| for reliability | for efficiency |

UDP / 6667
TCP / 80
TCP / 25565

![[Pasted image 20231107180223.png | 500]]

![[Pasted image 20231107180259.png | 500]]

---
# Layer 5, 6, 7 - Session, Presentation, Application

- three layers are Considered as single universal Application Layer.
- TCP/IP combines all the 3 layers into a single layer.
![[Pasted image 20231107181306.png | 400]]

---
# Data flow through all the layers

<iframe width="560" height="315" src="https://www.youtube.com/embed/0aGqGKrRE0g?si=beL734zLQRmPr_LP&amp;start=509" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

---

Sending - Encapsulation process

1. Application - Transport Layer (L4) ==> TCP + DATA (Segment)

	TCP header for service to service delivery, is added to the data.
	includes src port and dst port with the particular data.

2. Transport Layer - Network Layer (L3) ==> IP + TCP + DATA (Packet)
	
	goal of L3 Layer which is adding IP header for end to end delivery which includes src IP and dst IP

3. Network Layer - Data Link Layer (L2) ==> MAC + IP + TCP + DATA (Frame)

	goal of L2 Layer which is adding MAC header for hop to hop delivery which includes src MAC and dst MAC

4. Data Link Layer - Physical Layer (L1) ==> converts frame to binary


receiving host will do de-Encapsulation - Receiving process. The opposite work is done here.

---

![[Pasted image 20231107183118.png]]

---