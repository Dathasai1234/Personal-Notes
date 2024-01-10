---
title: CCNA
date: 2023-12-26
resources: 
tags:
  - IP-address
  - host-addresses
  - network-addresses
  - class-B-range
  - network-address
  - public-IPs
---
- assigned to medium and large-scaled networks
- the two high-order bits in a class B are always set to binary 1 0.
- ![[Pasted image 20231226110705.png]]
- default subnet mask is /16

---
# Valid range

- *network* addresses range
	- 128.0.0.0 / 16
	- 191.255.0.0 / 16
- *host* addresses range
	- 128.0.0.0 / 16
	- 128.255.255.255 / 16

- number of *networks*
	- 16,384
	- Because the first 2 bits of a Class B address are always 10, 14 bits are left in the network portion of the address, resulting in 214 or 16,384
	- [source](https://www.ciscopress.com/articles/article.asp?p=330807&seqNum=2#:~:text=Because%20the%20first%202%20bits%20of%20a%20Class%20B%20address%20are%20always%2010%2C%2014%20bits%20are%20left%20in%20the%20network%20portion%20of%20the%20address%2C%20resulting%20in%20214%20or%2016%2C384)
- number of *hosts*
	- 65,534

---