---
title: Basics of networking
date: 2023-11-08
resources: 
tags:
  - networking
---

# Table of contents

- [[#intro|intro]]
- [[#Part A|Part A]]
- [[#Hosts vs Routers|Hosts vs Routers]]
	- [[#Hosts vs Routers#TERMINOLOGIES|TERMINOLOGIES]]
	- [[#Hosts vs Routers#Routing Table|Routing Table]]
- [[#Part B|Part B]]
- [[#Part C|Part C]]
	- [[#Part C#Hierarchy Routes|Hierarchy Routes]]

---

# intro

![[1- Networking Fundamentals#Routers]]

---

![[2- OSI model#Layer 2 MAC Address vs Layer 3 IP addresses]]

---

# Part A
# Hosts vs Routers

<iframe width="560" height="315" src="https://www.youtube.com/embed/AzXys5kxpAM?si=ogS5ymFvVqWRM_sj&amp;start=200" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

- Routers are connected to a network
	- Routers have an IP address and a MAC address on each Interface

---
## TERMINOLOGIES

- ! **node** - a device that implements IPv6 or IPv4
- ! **router** - a node that forwards IP packets not explicitly addressed to itself
- ! **host** - any node that is not a router.

---

- Routers forward packets <u>not destined to themselves</u> (unlike hosts)
- Routers maintain a map of all the networks they know about
	- Routing table

![[Pasted image 20231108142941.png | 500]]

## Routing Table

- Routing table can be populated via **three** methods
	- **Directly connected** - Routes for networks which are attached.
	- **Static Routes** - Routes manually provided by an administrator.
	- **Dynamic Routes** - Routes learned automatically from other Routes.

---
# Part B

- Routers have IP and MAC for each Network they are connected to.
- Routers have Routing tables - map of every network
	- populated with **Directly connected**, **Static Routes**, **Dynamic Routes**.
- Routes also have ARP tables - mapping of L3 and L2 address.
	- Everything with an Ip address has an ARP table.
	- ! Start Empty - populated as needed with network traffic. 

*Each Router*
- Looks up destination IP in Routing Table to determine Next-Hop IP
- Adds a L2 header with Destination MAC next Router’s MAC
	- Performs ARP as necessary.

---
# Part C

## Hierarchy Routes

<iframe width="560" height="315" src="https://www.youtube.com/embed/zmxLg4jV0ts?si=a8bf2HLCCM1g0QRD&amp;start=188" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

- Hierarchy allows for Route Summarization.
	- Reduce number of Routes in Routing Table.
	- Default Route - ultimate route summary.
		- 0.0.0.0/0 - every IPv4 address.
		- “for everything else, go here”.
- Easier to scale.
- More consistent connectivity


![[Pasted image 20231108154022.png | 600]]

---