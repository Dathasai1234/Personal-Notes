---
title: lab-7
date: 2023-12-05
Firewalls: https://learn.microsoft.com/en-us/azure/firewall/overview
IDS and IPS: https://www.google.com/search?q=ids+and+ips+in+firewall&ie=UTF-8#:~:text=An%20IDS%20is,remediate%20the%20incident.
IPS: https://www.geeksforgeeks.org/intrusion-prevention-system-ips/
IDS: https://www.geeksforgeeks.org/intrusion-detection-system-ids/
tags:
---
# Table of contents

- [[#Azure firewall|Azure firewall]]
	- [[#Azure firewall#priority of DNAT, SNAT…|priority of DNAT, SNAT…]]
- [[#Route table limitations|Route table limitations]]
- [[#Load-Balancers|Load-Balancers]]

# need to prepare

- subnet delegation, can we add NSG’s and route tables.
- VPN gateways use route based or policy based.
- In the NSG’s we are not writing any outbound rules, how the traffic goes outside
- #ACL-Access_Control_List in switches.
- #stateful_firewalls(next gen firewalls) and #stateless_firewalls.
- If we give an outbound, no need to give an inbound called *stateful firewalls*
- the 3-way hand shake concept can be an example of stateful architecture.
<br>
- IDS and IPS [source](https://www.google.com/search?q=ids+and+ips+in+firewall&ie=UTF-8#:~:text=An%20IDS%20is,remediate%20the%20incident.)

---
# Azure firewall

- [source](https://learn.microsoft.com/en-us/azure/firewall/overview)
- We can use layer 3 Ip address rules in NSG’s.
- We can also use IP, urls and main more as rules.
- L3-L7, we can inspect the traffic.

- 3 types of Azure firewalls
	- Basic
	- Standard
	- Premium

- need to do subnet delegation for firewall.
- AzureFirewallSubnet
- \26
- We have a public Ip for a firewall
- We can use NAT rules, Network rules, Application rules concepts using firewalls.
- ![[Pasted image 20231205174308.jpg]]
- SNAT, DNAT
## priority of DNAT, SNAT…

Rule collection Group

DNAT (more priority)

N/W (medium priority)

Application (less priority).

---

# Route table limitations

- cannot associated to a different subscription subnet.

---
# Load-Balancers

[[public-Load-balancers]]