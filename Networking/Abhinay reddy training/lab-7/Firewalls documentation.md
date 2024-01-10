---
title: lab-7
date: 2023-12-05
resources: 
tags:
  - firewall
  - nat_rules
  - network_collection_rules
  - network-lab
---
# Table of contents

- [[#LAB|LAB]]
- [[#Do’s|Do’s]]
- [[#AD Authentication to connect Local machine|AD Authentication to connect Local machine]]
- [[#vm|vm]]
- [[#firewall|firewall]]
- [[#VPN|VPN]]
- [[#Resource Visualizer|Resource Visualizer]]
- [[#firewall|firewall]]
	- [[#firewall#DNAT|DNAT]]
	- [[#firewall#Network Rules|Network Rules]]
- [[#Routes|Routes]]
- [[#Route table at <u>VM subnet</u>|Route table at <u>VM subnet</u>]]
- [[#Communications|Communications]]
	- [[#Communications#VM to Local Machine|VM to Local Machine]]
	- [[#Communications#Local Machine to VM through Firewall|Local Machine to VM through Firewall]]


 
---
# LAB

![[Pasted image 20231213160111.png |700]]

[[arc-firewall-lab-architecture]]

---
# Do’s

- pinging through firewall.
- Route table is associated to VM subnet
- A P2S VPN is established to the VPN gateway subnet of Vnet.

---
# AD Authentication to connect Local machine

![[AD Authentication#AD authentication]]

---
# vm

**vm username -** Datha
**vm password -** Donotshare@vm

**vm public ip -** 172.203.249.54 (disassociated)
**vm private ip -** 10.0.1.4

---
# firewall 

**private ip -** 10.0.2.4
**public ip -** 20.124.209.186

---
# VPN

**address pool -** 192.168.1.0/24
**local machine ip allocated -** 192.168.1.2

---
# Resource Visualizer

![[firewall-lab-2.png | 500]]
![[arc-firewall-lab-architecture]]


---
# firewall

## DNAT

![[firewall-dnat.png | 700]]

## Network Rules

![[Pasted image 20231213155458.png | 700]]

---
# Routes

# Route table at <u>VM subnet</u>
![[Pasted image 20231213160402.png | 300]]

---
# Communications

## VM to Local Machine

![[Pasted image 20231213155618.png | 400]]

## Local Machine to VM through Firewall

![[Pasted image 20231213155701.png | 400]]

---