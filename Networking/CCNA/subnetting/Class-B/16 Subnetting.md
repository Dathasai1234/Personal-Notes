---
title: Class-B
date: 2024-01-11
resources: 
tags:
---
# 135.15.0.0/16

![[Pasted image 20240111124500.png]]

- If we subnet this into /29 subnets
- number of hosts - 3
$$
2^3 = 8
$$
$$
8 - 2 = 6
$$
- same number of hosts in case of **/A**, **/B** and **/C**
	- /B - 11111111 11111111 00000000 00000000
	- /29 - 11111111 11111111 11111111 11111000
	- subnet mask - 255.255.255.248
	- 135.15.0.0/16 - 10000111.00001111.00000000.00000000
<br>
- number of networks - 13 bits
$$
2^{13} = 8192
$$
<br>
- IP Address:	*135.15.10.138*
- **10000111.00001111.00001010.10001**010
- **11111111 11111111 11111111 11111**000
- 255.255.255.248
- 256-248 = 8
- Network address - 135.15.**10.136**
- usable address - 135.15.**10.137** - **142**
- Broad-cast address - 135.15.**10.143**

---

[[Quick Subnetting]]