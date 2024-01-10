---
title: CCNA
date: 2023-12-26
resources: 
tags:
  - subnetting
---
- Let’s say we’ve been allocated Class C *200.15.10.0/24*
- To subnet the network into smaller subnets, <u>we need to ‘borrow’ host bits and add them to the network portion of the address</u>.
- The network address line always <u>moves to the right</u> when we subnet.
- ! The further to the right we go, the more subnets we’ll have of that size but less hosts.

---
# Formulas

## calculate the <u>number of subnets</u>

- ! 2 ^ (subnet_bits)

e.g: source : [[08-03+Subnetting+Overview.pdf#page=3&selection=6,0,25,27|08-03+Subnetting+Overview, page 3]]

- If a **Class C network uses a /28 subnet mask** then we've *borrowed 4 bit* from the default of /24
- $ 2^4 = 16 available subnets
- If a **Class B network uses a /28 subnet mask** then we've *borrowed 12 bits* from the default of / 16
- $ 2^12 = 4096 available subnets
<br>
- Hosts on different subnets need to go via a router if they want to communicate with each other

---
## Calculate the <u>number of hosts</u>

- ! (2 ^ host_bits) - 2

- We subtract 2 because the network address and broadcast address cannot be assigned to hosts
<br>
- If a **Class C network uses a /28 subnet mask** then we *have 4 bits* left for hosts
	- $ 2^4-2=14
- If a **Class B network uses a /28 subnet mask** then we *have 4 bits* left for hosts
	- $ 2^4-2=14

---
# Class C /31 Subnet

- ! subnet mask for /31 = 255.255.255.254
- ! Binary Subnet Mask = 11111111.11111111.11111111.11111110

- 7 bits of network bits.
- 1 host bit.

## Number of subnets

2 ^ 7 = 128.

## Number of Hosts

2 ^ 1 = 2

### Number of usable hosts

2 ^ 1 - 2 = 0

---
# Class C /30 Subnet

- ! subnet mask for /30 = 255.255.255.252
- ! Binary Subnet Mask = 11111111.11111111.11111111.11111100

- 6 bits of network bits.
- 2 host bit.

## Number of subnets

2 ^ 6 = 64.

## Number of Hosts

2 ^ 2 = 4

### Number of usable hosts

2 ^ 2 - 2 = 2

---
# Class C /29 Subnet

- ! subnet mask for /29 = 255.255.255.248
- ! Binary Subnet Mask = 11111111.11111111.11111111.11111000

- 5 bits of network bits.
- 3 host bit.

## Number of subnets

2 ^ 5 = 32

## Number of Hosts

2 ^ 3 = 8

### Number of usable hosts

2 ^ 1 - 2 = 6

---
# Class C /28 Subnet

- ! subnet mask for /28 = 255.255.255.240
- ! Binary Subnet Mask = 11111111.11111111.11111111.11110000

- 4 bits of network bits.
- 4 host bit.

## Number of subnets

2 ^ 4 = 16.

## Number of Hosts

2 ^ 4 = 16

### Number of usable hosts

2 ^ 1 - 2 = 14

---
# Class C /27 Subnet

- ! subnet mask for /31 = 255.255.224.
- ! Binary Subnet Mask = 11111111.11111111.11111111.11100000
- 

- 3 bits of network bits.
- 5 host bit.

## Number of subnets

2 ^ 3 = 8.

## Number of Hosts

2 ^ 5 = 32.

### Number of usable hosts

2 ^ 1 - 2 = 30

---
# Class C /26 Subnet

- ! subnet mask for /31 = 255.255.255.192
- ! Binary Subnet Mask = 11111111.11111111.11111111.11000000

- 2 bits of network bits.
- 6 host bit.

## Number of subnets

2 ^ 2 = 4.

## Number of Hosts

2 ^ 6 = 64

### Number of usable hosts

2 ^ 1 - 2 = 62

---
# Class C /25 Subnet

- ! subnet mask for /31 = 255.255.255.128
- ! Binary Subnet Mask = 11111111.11111111.11111111.10000000

- 1 bits of network bits.
- 7 host bit.

## Number of subnets

2 ^ 1 = 2.

## Number of Hosts

2 ^ 7 = 128

### Number of usable hosts

2 ^ 1 - 2 = 126

---
# Class C /24 Subnet

- ! subnet mask for /31 = 255.255.255.0
- ! Binary Subnet Mask = 11111111.11111111.11111111.00000000
- 

- 0 bits of network bits.
- 8 host bit.

## Number of subnets

2 ^ 0 = 1.

## Number of Hosts

2 ^ 8 = 256

### Number of usable hosts

2 ^ 1 - 2 = 0

---
# [[Practice Question-1.pdf]]

/26

2 * 2 network addresses = 4 networks
2 * 6 host addresses - 2 = 62 usable hosts
255.255.255.192/26

198.22.45.173 / 26

198.22.45.0   - 198.22.45.63 
198.22.45.64 - 198.22.45.127
**198.22.45.128 - 198.22.45.191**
198.22.45.192 - 198.22.45.255

---
# Practice Questions

1. **IP Address: 192.168.10.75/28**
    - Find the subnet mask, network address, broadcast address, and valid host addresses.
2. **IP Address: 172.16.45.92/27**
    - Determine the subnet mask in dotted decimal notation and find the network, broadcast, and valid host addresses.
3. **IP Address: 10.0.5.200/29**
    - Calculate the subnet mask, network address, broadcast address, and valid host addresses.
4. **IP Address: 192.168.2.45/30**
    - Find the subnet mask, network address, broadcast address, and the two valid host addresses.
5. **IP Address: 172.31.88.15/26**
    - Determine the subnet mask, network address, broadcast address, and valid host addresses.

## Solutions

1. **192.168.10.75/28**

	Subnet mask - 255.255.255.240
	**11111111.11111111.11111111.1111**0000

	**11000000.10101000.00001010.0100**1011

	Number of subnets - 16
	Number of usable Hosts - 14

	Network address - 192.168.10.64
	Broadcast address - 192.168.10.79

---

2. **172.16.45.92/27**

	Subnet mask - 255.255.255.224
	**11111111.11111111.11111111.111**00000

	**10101100.00010000.00101101.010**11100

	Number of subnets - 8
	Number of hosts - 32
	Number of usable hosts - 30

	Network address - 172.16.45.64
	Broadcast address - 172.16.45.94

---

3. **10.0.5.200/29**

	Subnet mask - 255.255.255.224
	**11111111.11111111.11111111.11111**000

	**00001010.00000000.00000101.11001**000

	Number of subnets - 32
	Number of hosts - 8
	Number of usable hosts - 6

	Network address - 10.0.5.200
	Broadcast address - 10.0.5.207

---

4. **192.168.2.45/30**

	Subnet mask - 255.255.255.252
	**11111111.11111111.11111111.111111**00

	**11000000.10101000.00000010.001011**10

	Number of subnets - 64
	Number of hosts - 4
	Number of usable hosts - 2

	Network address - 192.168.2.44
	Broadcast address - 192.168.2.47

---

5. **172.31.88.15/26**

	Subnet mask - 255.255.255.252
	**11111111.11111111.11111111.11**000000

	**10101100.00011111.01011000.00**001111

	Number of subnets - 4
	Number of hosts - 64
	Number of usable hosts - 62

	Network address - 172.31.88.0
	Broadcast address - 172.31.88.63

---