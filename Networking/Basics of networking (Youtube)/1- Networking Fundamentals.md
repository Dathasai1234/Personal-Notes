---
title: Basics of networking
date: 2023-11-07
resources: 
tags:
  - networking
---

# Table of contents

^6df126

- [[#Hosts|Hosts]]
- [[#ip-address|ip-address]]
- [[#Network|Network]]
	- [[#Network#internet|internet]]
- [[#Repeaters|Repeaters]]
- [[#HUB, Bridge, Switch|HUB, Bridge, Switch]]
	- [[#HUB, Bridge, Switch#Hub|Hub]]
	- [[#HUB, Bridge, Switch#Bridge|Bridge]]
	- [[#HUB, Bridge, Switch#Switches|Switches]]
- [[#Routers|Routers]]

---

# Hosts

- ! Hosts are any device which sends or receive traffic
- Anything that sends or receive traffic over a network.
- Hosts typically fall in one of two categories.
	1. Clients (initiate requests)
	2. Servers (respond to the requests)
- Relative to specific communication.

---
# ip-address

- ! identity of each host.
- you need an ip address to send or receive packets on a network.
- ip address are 32 bits
	- Bit = 1 or 0
	- Represented as four **octets**
	- ![[Pasted image 20231107150550.png | 300]]

---
# Network

- ! A network is what transports traffic between.
- Logical grouping of hosts which require similar connectivity.

## internet

- ! internet is the interconnection of bunch of networks.

---
# Repeaters

- ! Repeaters regenerate signals.
- Allows communications across greater distances.
- allows to connect devices which spans greater distances.

---
# HUB, Bridge, Switch

^674588

![[Pasted image 20231107151855.png | 300]]

- Connecting hosts directly to each other doesn’t scale.
- instead we create devices which could put at the center of every network and connect all the hosts to those devices
- and these devices would then handle funneling communication between different hosts.

![[Pasted image 20231107152326.png | 300]]

## Hub

- ! Hubs are simply multi-port Repeaters
- Repeaters regenerate signals. hubs do the same, except they do on multiple ports.
- Facilitates scaling communication between additional hosts.
- Everyone receives everyone else’s data.

![[Pasted image 20231107153415.png | 300]]

---
## Bridge

- ! Bridges sit between Hub-connected hosts

![[Pasted image 20231107153555.png | 300]]

- set sets of hosts interconnected by a hub.
- The bridge is meant to sit in between hub connected hosts.
- have only 2 hosts.
- bridge learn which hosts are on which side, which allows the bridge to contain the communication only to that side necessary.

|                                      |                                      |     |
| ------------------------------------ | ------------------------------------ | --- |
| ![[Pasted image 20231107154351.png]] | ![[Pasted image 20231107154406.png]] | ![[Pasted image 20231107154456.png]]    |

---
## Switches

- ! Switches facilitate communication **within** a network.
- Switches are a combination of Hubs and Bridges
- Multiple ports.
- Learns which hosts are on each port.

|                                      |                                      |     |
| ------------------------------------ | ------------------------------------ | --- |
| ![[Pasted image 20231107154909.png]] | ![[Pasted image 20231107154936.png]] | ![[Pasted image 20231107155659.png]]    |

^47e20f

---
# Routers

![[Pasted image 20231107160638.png | 400]]

- ! Routers facilitate communication **between** networks.
- Provides a traffic control point (security, filtering, redirecting).
- Routers learn which networks they are attached to
- Known as **Routes** - stored in a routing table.
- ! **Routing-table** - all networks a Router knows about.
- Have IP address in the Networks they are attached to.
- ! **Gateway** - each host’s way out of their local Network.

|                                                                                      |     |
| ------------------------------------------------------------------------------------ | --- |
| ![[Pasted image 20231107161902.png]] |  ![[Pasted image 20231107161744.png]] |     |

^7b1559




- Create the Hierarchy in Networks and the entire Internet.

![[Pasted image 20231107162545.png | 400]]

- ! Routing is the process of moving data between networks
	- ! A router is a device whose primary purpose is Routing

- ! Switching is the process of moving data within networks ^b22b56
	- ! A switch is a device who’s primary purpose is Switching. 

---