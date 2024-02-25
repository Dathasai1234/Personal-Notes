---
title: AVD
date: 2024-02-25
resources: 
tags:
---
- AVD Service.
	- PaaS Remote solution built in Azure
- Windows 10 Multi-user
	- Windows IO OS that allows multiple User sessions
	- Only available in Azure
- FSLogix
	- User profile solution 
	- Provides a consistent user Experience between multiple Desktops
- MSIX App Attach
	- Containerized version of Applications attach to a client OS

# Host Pool Types

The host pool is a collection of VMs used to host user connections.

- Personal Host pool
	- One to one mapping of host to VM
	- ![[Pasted image 20240225141344.png]]
- Pooled Host Pool
	- Multi session OS such as Windows Server or Windows 10 Multi-User host multiple user sessions
	- ![[Pasted image 20240225141327.png]]

- We have two options for configuring how AVD load balances, new client connections to *session host* and a *pooled host pool*.
	- Breadth-First Load Balancing.
	- Depth-First Load Balancing.

![[20240225-0848-33.2558490.mp4]]

