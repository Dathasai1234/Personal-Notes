---
title: CCNA
date: 2023-12-25
resources: https://www.ciscopress.com/articles/article.asp?p=330807&seqNum=2
tags:
  - IP-address
  - host-addresses
  - network-addresses
  - loop-back-ip-addresses
  - class-A-range
  - IANA
  - network-address
  - public-IPs
---
- The bigger the host portion of the network, the most hosts we can have.
- If the subnet mask is /8, we have 24 bits available to allocate to hosts
- if the subnet mask is /24, we only have 8 bits available to allocate to hosts.

---
# #IANA

- The global coordination of Internet IPv4 addressing is performed by #IANA (Internet Assigned Numbers Authority.)
- This is the way it was originally supossed to work.
- when a company wants to communicate on the internet, they apply for a range of IP addresses.
- If they have 6000 hosts, they ask for a range of IP addresses big enough to cover that, plus room for a growth.
- They then allocate their addresses to their hosts in their offices.

---
# classes

# class A

#class-A

- network range
	- $ 1.0.0.0 / 8 
	- $ 126.0.0.0 / 8
- host range
	- $ 1.0.0.0
	- $ 126.255.255.254

- number of *networks*
	- 126
- number of *hosts*
	- 2^24 : 16,777,214

- ![[Pasted image 20231226111312.png]]
---
# Reserved class A addresses

- signifies *this network*
	- ! 0.0.0.0/8
- cannot be assigned
	- ! 0.0.0.1
	- ! 0.255.255.255
- *Loopback address* for testing local computer.
	- 127.0.0.0 / 8
		- ! 127.0.0.1
		- ! 127.255.255.255

- This wiped out 33,554,428 addresses from the global address pool
- [[07-02+Class+A+IP+Addresses.pdf#page=6&selection=2,0,15,7|07-02+Class+A+IP+Addresses, page 6]]

- If the first bit of the first octet of an IP address is a binary 0, the address is a Class A address. With that first bit being a 0, the lowest number that can be represented is *00000000*, decimal *0*. The highest number that can be represented is *01111111*, decimal *127*. Any address that starts with a value between 0 and 127 in the first octet is a Class A address. These two numbers, 0 and 127, are reserved and cannot be used as a network address.

---
# Subnetting in class A

[[07-02+Class+A+IP+Addresses.pdf#page=7&selection=2,0,20,43|07-02+Class+A+IP+Addresses, page 7]]

---