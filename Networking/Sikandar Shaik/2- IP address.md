---
title: Sikandar Shaik
date: 2023-11-10
resources: 
tags:
  - networking
---


set of rules to follow to have a proper communication.
The internet which is a place where everyone is connected is completely built based on *TCP/IP* protocol.
*TCP/IP* is a Standard protocol used between computers and network devices for communication
each device in a network should be assigned with an address called an *IP address*.

# I.P addresses

## I.P v4

- i.p V4 is a 32 bit address in binary
- divided into 4 octants with dots.
- for our convenience, we are going to convert actual binary format to decimal format.

| class | range   |
| ----- | ------- |
| A     | 0-127   |
| B     | 128-191 |
| C     | 192-223 |
|       |         |
| D     | 224-239 | 
| E     | 240-255 |

---
# Network and Host Portions

IP address id divided into Network and Host Portion

Host : a specific device in the network
Network : set of devices

---

# Subnet-mask

Subnet Mask differentiates Network portion and Host Portion.

1 represents network
0 represents hosts

| Class   | N/H     | IP            |
| ------- | ------- | ------------- |
| Class A | **N**.*H.H.H* | 255.0.0.0     |
| Class B | **N.N**.*H.H* | 255.255.0.0   |
| Class C | **N.N.N**.*H* | 255.255.255.0 | 

---

# FLSM & VLSM

![[Pasted image 20231101165026.png | 500]]

--- 