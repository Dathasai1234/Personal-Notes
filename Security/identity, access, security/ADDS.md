---
title: identity, access, security
date: 2023-12-13
resources: 
tags:
---
# Keywords

- managed domain (for one-way synchronization from Entra ID to ADDS)
- Domain Services managed domain
	- unique namespace (domain name)
	- domain controllers (DC’s)
		- Azure platforms handle the DC’s as a part of the <u>managed domain</u>
- domain join
- group policy
- LDAP
- Kerberos/NTLM authentication

---

==Three ways we can move an application to the cloud==

- Subscribe to SaaS application.
- Rewrite existing application. (old to new authentication)
- Lift and shift on-premises apps to IaaS.

---

==Is lift-and-shift existing on-prem apps easy?==

![[Pasted image 20231213202308.png | 500]]

==How many orgs handle this today==

|                                             |                                      |
| ------------------------------------------- | ------------------------------------ |
| ![[Pasted image 20231213202518.png \| 300]] | ![[Pasted image 20231213202543.png \| 300]] |

They built a sync engine which synchronizes all the users, groups and apps from Entra ID to ADDS.

- we need to select a *vnet* (managed domain), inside which you expose the domain.
- Microsoft will take care of transferring all the users, grps, apps on your existing Azure AD tenant to this vnet or managed domain.
- If you need to enter the Vnet, you have 2 Ip addresses for Domain controllers.
- All the classic 