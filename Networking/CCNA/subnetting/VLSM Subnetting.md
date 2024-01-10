---
title: subnetting
date: 2024-01-07
resources: 
tags:
---
![[Pasted image 20240107175103.png | 700]]

# Do VLSM for this network Topology

![[Pasted image 20240107183625.png | 700]]

Given IP address - 200.15.10.0/24
## NewYork
### Sales

14 Hosts

/28

Available hosts - 2 ^ 4 = 16
usable hosts - 14

Network address - 200.15.10.64/28
200.15.10.65 - 200.15.10.78
Broadcast address - 200.15.10.79/28
### Eng

27 Hosts

/27

Available hosts - 2 ^ 5 = 32
usable hosts - 30

Network address - 200.15.10.0/27
200.15.10.1 - 200.15.10.30
Broadcast address - 200.15.10.31/27
## Boston

### Sales

7 Hosts

/28

Available hosts - 2 ^ 4 = 16
usable hosts - 14

Network address - 200.15.10.80/28
200.15.10.81 - 200.15.10.94
Broadcast address - 200.15.10.95/28
### Eng

28 Hosts

/27

Available hosts - 2 ^ 5 = 32
usable hosts - 30

Network address - 200.15.10.32/27
200.15.10.28 - 200.15.10.57
Broadcast address - 200.15.10.63/27

# point to point routers ips

2 Hosts

/30

Available hosts - 2 ^ 2 = 4
usable hosts - 2

Network address - 200.15.10.96/28
200.15.10.97 - 200.15.10.98
Broadcast address - 200.15.10.99/28

---

|Department|Branch|Network Address|Broadcast Address|
|---|---|---|---|
|Sales|New York|200.15.10.64/28|200.15.10.79|
|Sales|Boston|200.15.10.80/28|200.15.10.95|
|Engineering|New York|200.15.10.0/27|200.15.10.31|
|Engineering|Boston|200.15.10.32/27|200.15.10.63