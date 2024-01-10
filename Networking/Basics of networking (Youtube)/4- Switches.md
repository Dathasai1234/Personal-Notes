---
title: Basics of networking
date: 2023-11-08
resources: https://www.youtube.com/watch?v=G7GyWjJtjNs&list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi&index=8&pp=iAQB
tags:
  - networking
---
# Table of contents

- [[#PART A|PART A]]
	- [[#PART A#How switches facilitate communication in a network|How switches facilitate communication in a network]]
- [[#Traffic going THROUGH the switch vs TO the switch|Traffic going THROUGH the switch vs TO the switch]]
- [[#PART B|PART B]]
	- [[#PART B#Unicast Frame vs Broadcast Frame|Unicast Frame vs Broadcast Frame]]
- [[#VLANs - Virtual Local Area Networks|VLANs - Virtual Local Area Networks]]
	- [[#VLANs - Virtual Local Area Networks#How switches operate when multiple switches involve|How switches operate when multiple switches involve]]

---

- ! Switches use and maintain **MAC ADDRESS TABLE**
- ! Switches perform three actions **LEARN, FLOOD, FORWARD** 

# PART A

![[1- Networking Fundamentals#^b22b56]]

![[1- Networking Fundamentals#^47e20f]]

![[Pasted image 20231107201411.png | 500]]

- Switches are L2 devices - they only use L2 header to make decisions.

## How switches facilitate communication in a network

- ! use and maintain **MAC Address Table**
	- Mapping of switch ports to MAC Addresses

|                                      |                                      |
| ------------------------------------ | ------------------------------------ |
| ![[Pasted image 20231108121643.png]] | ![[Pasted image 20231108121519.png]] |
|                                      |                                      |

- ! Switches perform three actions
	- **Learn** - Update MAC Address Table with Mappings of Switch Port to Source Port
	- **Flood** - Duplicate and send frame out all switch ports (except receiving port)
	- **Forward** - Use MAC Address Table to deliver Frame to appropriate switch port

- Process would be identical if host was a router connected to the internet.

# Traffic going THROUGH the switch vs TO the switch

- Switch has a MAC address and is configured with an IP address
- Switch essentially acts as a host in the network (follows all the communication rules)

---
# PART B

## Unicast Frame vs Broadcast Frame

| Unicast                                                           | Broadcast                           |
| ----------------------------------------------------------------- | ----------------------------------- |
| Switch will flood only if MAC address is not in MAC address table | Broadcast frames are always Flooded | 

- ! Flood - type of action switch takes.
- Broadcast - Type of Frame.
- ! Switch will do **Learn, Flood, Forward** actions but not **broadcast**.
- Switches will only send broadcasts if traffic is going TO or FROM the switch.

---
# VLANs - Virtual Local Area Networks

- Divides Switch ports into isolated groups
- Divides Switches into multiple “mini-switches”
- Switches do all three actions within each VLAN

|     |                                      |
| --- | ------------------------------------ |
| ![[Pasted image 20231108125352.png]]    | ![[Pasted image 20231108125512.png]] |

---
## How switches operate when multiple switches involve


<iframe width="560" height="315" src="https://www.youtube.com/embed/G7GyWjJtjNs?si=BjYJpLzcyWiItd_O&amp;start=314" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

---