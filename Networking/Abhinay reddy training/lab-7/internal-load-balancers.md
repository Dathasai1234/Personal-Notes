---
title: lab-7
date: 2023-12-20
resources: https://www.youtube.com/watch?v=EhFV4eStj3g
tags:
  - internal-load-balancer
  - load-balancer
  - backend-pools
  - Frontend-IP
  - Health-probes
  - load-balancer-rules
---
# Table of contents

- [[#Load-balancer analysis|Load-balancer analysis]]
- [[#IP-schema|IP-schema]]
	- [[#IP-schema#Load-balancer|Load-balancer]]
- [[#VM’s|VM’s]]
	- [[#VM’s#VM-1 <u>NIC</u>|VM-1 <u>NIC</u>]]
	- [[#VM’s#VM-2 <u>NIC</u>|VM-2 <u>NIC</u>]]

# Architecture

![[arc-internal-load-balancer]]
[[arc-internal-load-balancer]]

---
# Load-balancer analysis

![[Pasted image 20231220185710.png | 500]]

---
# IP-schema

## Load-balancer

- ### Frontend-IP config
	- 10.0.0.134
- ### Backend-pools
	- b1
		- ![[Pasted image 20231220185938.png | 900]]
	- b2
		- ![[Pasted image 20231220190014.png | 900]]
- ### Health-Probes
	- one for two.
	- ![[Pasted image 20231220190214.png | 500]]
	- used by h1 and h2, which means the <u>single health probe is used by two load-balancer rules</u>
- ### Load-balancing rules
	- h1
		- ![[Pasted image 20231220191255.png | 500]]
	- h2
		- ![[Pasted image 20231220191331.png | 500]]

---
# VM’s

## VM-1 <u>NIC</u>

| Priority | Name                          | Port | Protocol | Source            | Destination    | Action |     |
| -------- | ----------------------------- | ---- | -------- | ----------------- | -------------- | ------ | --- |
| 300      | RDP                           | 3389 | TCP      | Any               | Any            | Allow  |     |
| 310      | AllowAnyHTTPInbound           | 80   | TCP      | Any               | Any            | Allow  |     |
| 65000    | AllowVnetInBound              | Any  | Any      | VirtualNetwork    | VirtualNetwork | Allow  |     |
| 65001    | AllowAzureLoadBalancerInBound | Any  | Any      | AzureLoadBalancer | Any            | Allow  |     |
| 65500    | DenyAllInBound                | Any  | Any      | Any               | Any            | Deny   |     |

## VM-2 <u>NIC</u>

| Priority | Name                          | Port | Protocol | Source            | Destination    | Action |     |
| -------- | ----------------------------- | ---- | -------- | ----------------- | -------------- | ------ | --- |
| 300      | RDP                           | 3389 | TCP      | Any               | Any            | Allow  |     |
| 320      | HTTPS                         | 443  | TCP      | Any               | Any            | Allow  |     |
| 65000    | AllowVnetInBound              | Any  | Any      | VirtualNetwork    | VirtualNetwork | Allow  |     |
| 65001    | AllowAzureLoadBalancerInBound | Any  | Any      | AzureLoadBalancer | Any            | Allow  |     |
| 65500    | DenyAllInBound                | Any  | Any      | Any               | Any            | Deny   |     |

---

- $ The **Http** traffic is hitting **VM1** through the Firewall.
- ! The **Https** is not hitting **VM2** through the Firewall, as the servers are configured for port number **80** (HTTP), not for **443** (HTTPs).
<br>
- Two **backend pools** are created, and each VM, VM1 and VM2 are attached to the backend pools.
- The two backend pools are connected to the same health probe which uses **port 80** to send message packets to <u>acknowledge the health status</u>.
- ! The health status of VM2 degrades to 50%, because the web servers <u>are not configured to HTTPS</u>. To recover the health status, re-configure the load-balancer-rules from <u>HTTPS to HTTP</u>.
- source : <iframe width="560" height="315" src="https://www.youtube.com/embed/EhFV4eStj3g?si=P9iaFcNP7kImxN9B&amp;start=652" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
- 
![[Pasted image 20231220183802.png | 700]]

---