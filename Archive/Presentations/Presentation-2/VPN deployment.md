---
title: Presentation-2
date: 2024-01-03
resources: 
tags:
---

**10:47:11**

1. Create a *resource group*.
2. Create a *Virtual Network*.
	1. a *regular subnet* with enough IPs for your work space.
	2. a delegated subnet called **GatewaySubnet** where we deploy a *Virtual network Gateway*.
3. Create a *Virtual Machine Server* in your regular subnet.
4. a *Virtual Network Gateway* in delegated subnet.
# Basic Tab
![[Pasted image 20240103104713.png]]

---
# P2S Configuration

## Address Pool

An address pool is a range of ip address you want to reserve and allocate to your local machine.

## Tunnel Type

![[Pasted image 20240103112412.png | 500]]

## Authentication Type

![[Pasted image 20240103112633.png | 500]]


---