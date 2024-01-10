---
title: Presentation-1
date: 2023-11-13
resources: 
tags:
  - Compute
---

%%
# Requirements

## Basics

- Subscription
	- resource group

- VM name
- Region
- Ava opts
	- No infrastructure redundancy required
	- Availability zone
	- VM scale set
	- Availability set
- Security type
- Image
- VM architecture
	- Arm 64
	- **x64**
- Run with azure Spot discount
- Size
- Enable hibernation (preview)

- Authentication type
	- **SSH public key**
	- Password
- Username
- Password

- Public inbound ports
	- none
	- **Allow selected ports**
- Select inbound ports
	- SSH(22)
	- HTTP(80)
	- HTTPS(443)

## Disks

- OS disk size
	- Image default 30GiB
- OS disk type
	- Premium SSD
	- Standard SSD
	- Standard HDD
- Delete with VM
- Data disks

## Networking

- Vnet
- Pub IP
- NIC
	- None Basic Advanced

%%

---

- VM is a kind of server
- It can be a Windows server, Linux server(at kind of distro)
- Microsoft used HyperV (Its own tool) as implementation of virtualization to create a Virtual Machine.
- In VM’s there two categories
	- Basic Tier - (dev and Test Workloads)
		- Five Sizes
			- A0 to A4
	- Standard tier
		- General Purpose (only for free tire) A series
		- GPU
		- HPC
		- Compute
		- Memory
		- Storage
		- Confidential compute
		- FPGA
 
When you provision a VM, you’ll also have the chance to pick the resources that are associated with that VM, including:

