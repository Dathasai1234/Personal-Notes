---
title: public
date: 2023-12-26
resources: https://www.ciscopress.com/articles/article.asp?p=330807&seqNum=2
tags:
  - IP-classes
  - public-IPs
  - class-A-range
  - class-B-range
  - class-C-range
  - CIDR
---
| Address Class | 1st octant begins with      | First Octet Range | Number of Possible Networks | Number of Hosts Per Network |
| ------------- | --------------------------- | ----------------- | --------------------------- | --------------------------- |
| Class A       | **0**0000000 - **0**1111111 | 0 to 126          | 127 (2 are reserved)        | 16,777,214                  |
| Class B       | **10**000000 - **10**111111 | 128 to 191        | 16,384                      | 65,534                      |
| Class C       | **110**00000 - **110**11111 | 192 to 223        | 2,097,152                   | 254                         |
| Class D       | **1110**0000 - **1110**1111 | 224 to 239        |                             |                             |
| Class E       | **1111**0000 - **1111**1111 | 240 - 255         |                             |                             |

![[Pasted image 20231226163929.png]]

- 128
	- 128
- 64
	- 192 (128 + 64)
- 32
	- 224 (128 + 64 + 32)
- 16
	- 240 (128 + 64 + 32 + 16)
- 8
	- 248 (128 + 64 + 32 + 16 + 8)
- 4
	- 252 (128 + 64 + 32 + 16 + 8 + 4)
- 2
	- 254 (128 + 64 + 32 + 16 + 8 + 4 + 2)
- 1
	- 255 (128 + 64 + 32 + 16 + 8 + 4 + 2 + 1)

---
# #CIDR

- removed the fixed /8, /16, and /24 requirements for the address classes, and allowed them to be split or subnetted into smaller networks.
- i.e, 175.10.10.0 / 20
- companies can now be allocated an address range which can closely matches their needs and does not waste addresses
## benefit - 2

![[Pasted image 20231226165847.png]]

- ISP A does not know about all 256 /24 networks reachable in ISP B It only has the single 175.11.0.0/16 summary route
- This reduces the size of ISP A's routing table and takes up less memory
- If an individual link goes down in ISP B, it has no impact on ISP A.
- The single summary route does not change
- (Routers in ISP B would have to recalculate their routing table if a link went down)
- This restricts issues to the local part of the network and reduces CPU load

---
# resources

1. [[class A IP addresses]]
2. [[class B IP addresses]]
3. [[class C IP addresses]]
4. [[class D IP addresses]]
5. [[class E IP addresses]]