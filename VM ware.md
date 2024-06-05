---
title: 
date: 2024-06-04
resources: 
tags:
---

# Corporate Environment

![[Pasted image 20240604194252.png]]

# Home Environment

![[Pasted image 20240604194320.png]]

- There are two virtualization software
	- **VMWare Player** (workstation player)- Runs over an Operating System.
		- Personal or home use.
	- **VMWare hypervisor** - Bare-metal hypervisor runs over a hardware without having any OS.
		- Corporate use.

## Products of VMWare

- **Workstation player** - utility for running VM's on Windows, Linux or MAC computers.
- **VMWare vSphere Hypervisor (ESXi)** - Bare-metal hypervisor that installs directly  onto the physical server.
	- VMWare vSphere Hypervisor is an ESXi server.
- **VMWare vSphere Client** - Is an interface that allows you to connect to a hypervisor.
	- It is a client just like RDP for windows and putty for Linux servers.
	- It is now web-based client.
- **VMWare vCenter** - It's a management tool to manage multiple hypervisor.

## Design Considerations

![[VMware-design-1]]

- If the physical server fails to run and experiencing a down-time, the OS and apps will not run.
- There is no redundancy for OS and apps that run on it.

![[VMware-design-2]]

- Design with Redundancy.

- The below design is considered as the further lab.
![[VMware LAB]]

---
- Download the latest version of **VMware Workstation player**.
![[Pasted image 20240605164839.png]]

- Creating First VM on VMWare Player (Demo to crate a VM directly on VMware).
- Creating **vSphere ESXi hypervisor server** on VMware player. In the corporate environment, all the servers are created on top of ESXi servers.
	- We don't need to install VMware Player for corporate environment, to make this lab possible, the VMware player is installed.
	- In the corporate environment, we don't require VMware player and an OS running on a bare-metal server. The ESXi server is directly downloaded on top of bare-metal server.
- Install the iso file of **vSphere ESXi hypervisor server**.
![[Pasted image 20240605171518.png | 300]]

- The above interface is the ESXi configuration console.
	- Server name - ESXi-1
	- Clicking F2 will allow to change the configurations of the server.
	- Changing the Dynamic Ip address which is set to DHCP to static IP address. Click spacebar to select the option.
	- After the changes to the network configurations, click on restart Management Network.

- **Connecting to ESXi server** and Exploring **vSphere Dashboard**.
	- **vSphere Web client** is the client is used to connect ESXi server in order to create Virtual Machines.
	- Open the IP address on any web browser.

![[Pasted image 20240605174254.png]]
![[Pasted image 20240605174657.png]]
