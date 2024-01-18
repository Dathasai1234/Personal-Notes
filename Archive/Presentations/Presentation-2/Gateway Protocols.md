---
title: Presentation-2
date: 2024-01-03
resources: https://www.youtube.com/watch?v=G0qDnqOKwOE&list=PLJqb_j53o7BiVPaFGQxEHhGx-ximMukwH
tags:
  - External_Gateway_Protocol
  - interior_gateway_protocol
  - Border_Gateway_Protocol
---
# Index

- [[##IGP|#IGP]]
- [[##BGP|#BGP]]
- [[#Administrative distance|Administrative distance]]
- [[#BGP’s #Loop_Prevention_Mechanism.|BGP’s #Loop_Prevention_Mechanism.]]

![[Pasted image 20240103131722.png]] ^00f052

- An #Autonomous_Systems is a Collection of networks under a single technical administration ^7df8bc
- #IGP’s #interior_gateway_protocol operate within an AS
- #BGP is only an #External_Gateway_Protocol which is used between an AS
- Exchange of loop-free routing information is guaranteed

# #IGP 

- These are the protocols operate within the AS
	- Static Routing
	- Default Routing
	- Dynamic Routing
		- RIP
		- EIGRP
		- OSPF
		- ISIS

**04-01-2024**
**11:32:55**

# #BGP 

- It is an **Exterior Gateway Protocol**
- Open Standard
- Designed for **Inter-AS Domain Routing**
- Designed to scale huge inter-network like internet.
- Classless.
	- Support FLSM, VLSM, CIDR, auto and manual summary (BGP-4)
- Updates are incremental and trigger
- Also called as #Path_vector_protocol
	- method of sending the routes with path information
	- ![[Pasted image 20240104120100.png | 500]]

- It send updates to manually defined neighbor as unicast
	- 3 way handshake will not happen, the connection configuration is done manually on both sides.
- BGP is **application layer protocol** uses TCP for reliability, TCP port 179
- #Administrative_distance ^9d8dd4
	- 20 External updates (EBGP)
	- 200 Internal updates (IBGP)

---
# Administrative distance

^b0734c

#Administrative_distance is a concept used in routing protocols to assign a measure of trustworthiness or preference to different routing information sources. It is a way **to prioritize which routing information to use when there are multiple sources of routing information available**. In the context of Border Gateway Protocol (BGP), administrative distance is <u>used to compare routes learned from different sources</u>, and the route with the <u>lowest administrative distance is preferred</u>.

In BGP, routes can be learned from various sources, such as:

1. **External BGP (eBGP):** Routes learned from BGP peers outside of the local autonomous system.
    
2. **Internal BGP (iBGP):** Routes learned from BGP peers within the same autonomous system.
    
3. **Static Routes:** Manually configured static routes.
    
4. **Directly Connected Routes:** Routes learned from directly connected networks.
    

The administrative distance is a numerical value assigned to each of these sources, and the route with the lowest administrative distance is considered the most preferred. If there are multiple routes to the same destination, BGP will select the route with the lowest administrative distance.

Here are the typical administrative distance values for BGP:

- **External BGP (eBGP):** 20
- **Internal BGP (iBGP):** 200
- **Static Routes:** 1
- **Directly Connected Routes:** 0

So, for example, if there are multiple routes to a particular destination learned from both eBGP and iBGP, BGP will prefer the route learned from eBGP due to its lower administrative distance.

---
# BGP’s #Loop_Prevention_Mechanism.

^7da1a6

![[Pasted image 20240104123439.png | 600]]

to ensure that routing information does not circulate endlessly in the network, causing instability and inefficiency. BGP uses a few key mechanisms to prevent loops:

#AS_Path_Attribute: One fundamental loop prevention mechanism in BGP is the AS Path attribute. The AS Path attribute is a list of AS numbers that a route has traversed to reach the current AS. When a BGP router receives an update, it checks the AS Path to ensure that its own AS number is not present in the list. If the router finds its own AS number in the AS Path, it knows that a routing loop has occurred, and it will reject that route to prevent the loop.

---