---
title: Migration
date: 2024-01-29
resources: 
tags:
  - EC2
  - onboarding
  - ARC
  - ARC-Machine
---

# Index

- [[#Icons|Icons]]
	- [[#Icons#Onboarding Servers to Azure ARC|Onboarding Servers to Azure ARC]]
- [[#ARC Lab|ARC Lab]]
	- [[#ARC Lab#EC2 Instance in *AWS*|EC2 Instance in *AWS*]]
	- [[#ARC Lab#Onboarding to Azure Using *ARC*|Onboarding to Azure Using *ARC*]]
	- [[#ARC Lab#Onboarded EC2 to Azure as Azure Resource|Onboarded EC2 to Azure as Azure Resource]]
	- [[#ARC Lab#We Can Manage and Monitor the EC2 in Azure|We Can Manage and Monitor the EC2 in Azure]]


> [!note] 
> "Azure ARC is a service or an offering in Microsoft Azure, which provides a centralized management of all the resources that exists in on-prem environment and multi-cloud environment"

# Icons

![[00756-icon-service-Azure-Arc.svg | 100]] - Arc icon  ![[01710-icon-service-Arc-Machines.svg | 100]] - Azure Arc - server ![[10021-icon-service-Virtual-Machine.svg | 100]] - Azure VM

---

- "Azure ARC services are specifically designed to onboard Non-Azure resources to Azure".
- ![[Pasted image 20240129191748.png]]

- ![[Pasted image 20240129191937.png]]

- ! When you use Azure ARC to onboard Non - Azure resource to Azure, these non-Azure Resources will get onboarded as Azure Resource
- ![[Pasted image 20240129194254.png]]

---
## Onboarding Servers to Azure ARC

- You just need to install Azure ARC client on supported version of servers, and that's it
- Your Servers will be onboarded to Azure as resource
- Then you can use different control which Azure ARC for servers has to offer.
- ant is small.
- elephant is big.

---
# ARC Lab

## EC2 Instance in *AWS*

![[Pasted image 20240130163207.png]]
## Onboarding to Azure Using *ARC*

![[Pasted image 20240130163303.png]]
## Onboarded EC2 to Azure as Azure Resource

![[Pasted image 20240130163336.png]]

## We Can Manage and Monitor the EC2 in Azure

![[Pasted image 20240130163413.png]]

- The policies and defender can work on that EC2 instance.

## EC2 in Defenders Inventory

![[Pasted image 20240130164015.png]]