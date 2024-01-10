---
title: Sikandar Shaik
date: 2023-11-13
resources: https://youtu.be/jJ8ifk0gSR8?list=PLJqb_j53o7BhRrYwLDy41AwR4pm-5nWk4
tags:
  - networking
---
- minimizes the wastage of IP addresses
- 2 methods
	- **FLSM**
	- **VLSM**

> [!important] Formulas
> Subnetting can be done based on the requirement.
> Requirement of Hosts?
> 	***2^h - 2 ≥ requirement***
> Requirement of Networks?
> 	***2^n ≥ requirement***
> Number of Subnets
> 	***2^number of host bits***

^de2d93

---
# What we do in Subnetting

- Converting Host into Network Bits (reduce number of host bits)
- Converting 0’s into 1’s.

---
# Exercise
## C-class, Req = 50 hosts (FLSM)


![[3- subnetting#^de2d93]]

![[Pasted image 20231113113146.png | 300]]

2^6 - 2 ≥ 50.
**62** - Valid Hosts

### Required Host Bits

power value will be the host bits.
**6**

**Number of Subnets** - 2^2 = **4**.

N.N.N.H
11111111  .  11111111  .  11111111  .  11000000
8 + 8 + 8 + 2 = **26 Network bits** 

Class B = 24/8 => **26/6**

**Subnet mask** - **255  .  255  .  255 . 192**

### Range (Size of the network)

![[3- subnetting#^de2d93]]

2^h = 2^6 = **64 Networks**

### Number of Networks

- 0 - 63
- 64 - 127
- 128 - 191
- 192 - 255

---
# Ip addresses

- an ip address is a 32 bit binary form.
- the address can be divided into 4 octets.