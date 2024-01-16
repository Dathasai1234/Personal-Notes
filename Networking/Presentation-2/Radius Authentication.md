---
title: Presentation-2
date: 2024-01-04
resources: 
tags:
  - network-lab
  - VPN
  - P2S
  - Radius-Authentication
---
# Pre-requisites

- A RouteBased VPN gateway.
- A #RADIUS server to handle user authentication.
	- The RADIUS server can be deployed on-premises, or in the Azure VNet.
	- You can also configure two RADIUS servers for high availability.
- The VPN client profile configuration package is a package that you generate. It provides the settings required for a VPN client to connect over P2S.

---
# Radius server configuration

- Go to tools
- Computer Management
	- Local users and Groups
		- Groups
			- Add a New Group
				- VPN
				- ![[Pasted image 20240104170327.png | 400]]
		- Users
			- Add a New User
				- ! Username: Blue
				- ! Password: donotshare@Radius
				- $ These are used when you download VPN client.
				- ![[Pasted image 20240104170714.png | 400]]
		- Add the new user to the new group
- Manage > Add Roles and Features
- Install Network Policy and Access Services Tools
- Tick the Restart the destination server automatically if required in Conformation tab
- Install
<br>
- Go to Tools > Network Policy server
- ![[Pasted image 20240104171404.png | 500]]
- We will create a policy to allow the Remote network access to the users in the newly created group <u>VPN</u>.
- Policies > Network-policies > new.
	- policy name - AzureVPN
	- Type of network access server - VPN-Dial up
	- ![[Pasted image 20240104171834.png | 500]]
	- Next
- Add a condition
	- Add user Groups
		- Add the group you have created
- ![[Pasted image 20240104172627.png | 500]]
- Confirm that your new policy has been created
- ![[Pasted image 20240104172834.png | 800]]
<br>
- Create a new Radius Client
	- Click on Radius Clients and Servers
	- new
	- Friendly-name : Radius Client
	- Address (IP or DNS): enter the subnet of Vnet Gateway
	- ! Shared secret (remember it): -------
	- $ used when you configure P2S in Vnet Gateway

---

- Configure point 2 site in Vnet gateway.
- Authentication type : RADIUS authentication
- Primary Server IP address : RADIUS configured VM Private IP address.
- Save it and download VPN client.

---

- From Local server, hit the RDP of internal Host private IP. It will open.

---
![[Pasted image 20240104193507.png | 300]]

---
# Things to remember

- Use VPN-client application which you have downloaded from Microsoft Store.
- That application is only used for AD authentication, Not for certificate authentication and Radius Authentication.