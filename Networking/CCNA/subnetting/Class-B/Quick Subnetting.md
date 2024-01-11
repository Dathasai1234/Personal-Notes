---
title: Class-B
date: 2024-01-11
resources: https://community.infosecinstitute.com/discussion/67245/quick-subnetting-all-in-your-head
tags:
---
# Question

**Question:** What's the 
*subnet number*, 
*broadcast address*, and 
*host range* of the below address?
- 172.21.92.251
## number of Subnets

Class B address.
10101100.00010101.01011100.11111011
/20
11111111.11111111.11110000.00000000
subnet mask - 255.255.**240**.0

- Take a look at each octet in the mask and see if it's a 255, 0, or some other number.
- If the octet is neither a 255 or 0, that's your interesting octet.
- In our case, in red, shows the interesting octet.
<br>
- compare the mask to the IP address.
	- 172.21.92.251
	- 255.255.**240**.0
- Anything on the left of the interesting octet, signals that you should copy the IP address octet to your subnet number.
- (X means it's currently unknown)
	- **172.21**.X.X
<br>
- Anything on the right of the interesting octet, signals that you should copy a 0 down into the subnet number.
	- **172.21**.X.**0**
<br>
- All that's left to find is the value of the interesting octet for our subnet number.
- This part is a little confusing at first, but will get easier with practice.
- The first step is to calculate the magic number.
- There's nothing magic about it, but it has many uses.
- To find the magic number, simply subtract the number 256 from the interesting octet in the mask.
	- 256 - 240 = **16**
<br>
- Next you need to take the magic number and find the multiples of this number that is closest to or less than the interesting octet in the IP address.
- This can be done easy by doubling the magic number until you have a number that is closest to/equal to but not more than the interesting octet in the IP address.
- Since our interesting octet in the IP address is **92** you'll find the multiples as follows.
- 172.21.**92**.251
	- 16, 32, 48, 64, **80**, 96
<br>
- As you can see, 80 is the closest number to 92 without actually going over 92.
- Guess what? We now have our subnet number. Simply place 80 in the interesting octet.
	- 172.21.**80**.0
<br>
- Finding the **broadcast address** is very easy.
- You again deal with the interesting octet first, but you're now using the subnet number that we just found out.
- Simply take the interesting octet (80) and add the magic number (16) then subtract 1.
- This gives you your interesting octet for the broadcast address.
	- 80 + 16 - 1 = **95**
<br>
- Lastly, anything to the right of your interesting octet will now change from 0 to 255. Now you have your broadcast address. 
	- 172.21.95.255
	  
Lets pull together what we have.  
Subnet Number - _172.21.80.0_  
Broadcast Address - _172.21.95.255_  
  
- To find the host range, simply add 1 to the final octet of the subnet number and subtract 1 from the final octet of the broadcast address.  
	- **Host Range -** **172.21.80.1 - 172.21.95.254**  
	  
And now you have your subnet number, broadcast address, and host range without having to use any binary. If you practice this a few times you'll find it very easy to do in your head. This will help you answer mostly any subnetting question on the ICND1 test.

---
# Normal

172.21.92.251
**10101100.00010101.0101**1100.11111011
/20 w.r.t /16
**11111111.11111111.1111**0000.00000000

number of subnets - 
$$
2^4 = 16
$$
number of hosts - 
$$
2^{12} = 4096
$$
network address - 172.21.80.0
usable ips - 172.21.80.1 to 172.21.80.254
broadcast address - 172.21.95.255

---
