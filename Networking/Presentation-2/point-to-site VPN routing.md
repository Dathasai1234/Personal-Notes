---
title: Presentation-2
date: 2024-01-16
resources: https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-point-to-site-routing
tags:
---
# Index

- [[#One isolated VNet|One isolated VNet]]
	- [[#One isolated VNet#Address space|Address space]]
	- [[#One isolated VNet#Routes added|Routes added]]
	- [[#One isolated VNet#Access|Access]]
- [[#Multiple peered VNets|Multiple peered VNets]]
	- [[#Multiple peered VNets#Address space:|Address space:]]
	- [[#Multiple peered VNets#Routes added|Routes added]]
	- [[#Multiple peered VNets#Access|Access]]
- [[#Multiple VNets connected using an S2S VPN|Multiple VNets connected using an S2S VPN]]
	- [[#Multiple VNets connected using an S2S VPN#Address space|Address space]]
	- [[#Multiple VNets connected using an S2S VPN#Routes added|Routes added]]
	- [[#Multiple VNets connected using an S2S VPN#Access|Access]]
- [[#Multiple VNets connected using an S2S VPN (BGP)|Multiple VNets connected using an S2S VPN (BGP)]]
	- [[#Multiple VNets connected using an S2S VPN (BGP)#Address space|Address space]]
	- [[#Multiple VNets connected using an S2S VPN (BGP)#Routes added|Routes added]]
	- [[#Multiple VNets connected using an S2S VPN (BGP)#Access|Access]]

# One isolated VNet
![[Pasted image 20240116170259.jpg]]
## Address space

- VNet1: 10.1.0.0/16
## Routes added

- Routes added to Windows clients: 10.1.0.0/16, 192.168.0.0/24
- Routes added to non-Windows clients: 10.1.0.0/16, 192.168.0.0/24
## Access

- Windows clients can access VNet1
- Non-Windows clients can access VNet1

---
# Multiple peered VNets

![[Pasted image 20240116170506.jpg]]

## Address space:

- VNet1: 10.1.0.0/16
- VNet2: 10.2.0.0/16
- VNet3: 10.3.0.0/16
- VNet4: 10.4.0.0/16
    
## Routes added

- Routes added to Windows clients: 10.1.0.0/16, 10.2.0.0/16, 10.4.0.0/16, 192.168.0.0/24
- Routes added to non-Windows clients: 10.1.0.0/16, 10.2.0.0/16, 10.4.0.0/16, 192.168.0.0/24
## Access

- Windows clients can access VNet1, VNet2, and VNet4, but the VPN client must be downloaded again for any topology changes to take effect.
- Non-Windows clients can access VNet1, VNet2, and VNet4

---
# Multiple VNets connected using an S2S VPN

![[Pasted image 20240116170601.jpg]]

## Address space

- VNet1: 10.1.0.0/16
- VNet2: 10.2.0.0/16
- VNet3: 10.3.0.0/16
  
## Routes added

- Routes added to Windows clients: 10.1.0.0/16, 192.168.0.0/24
- Routes added to Non-Windows clients: 10.1.0.0/16, 10.2.0.0/16, 192.168.0.0/24
## Access

- Windows clients can only access VNet1
- Non-Windows clients can access VNet1 only

---
# Multiple VNets connected using an S2S VPN (BGP)

![[Pasted image 20240116170649.jpg]]

## Address space

- VNet1: 10.1.0.0/16
- VNet2: 10.2.0.0/16
- VNet3: 10.3.0.0/16
    
## Routes added

- Routes added to Windows clients: 10.1.0.0/16, 192.168.0.0/24
- Routes added to Non-Windows clients: 10.1.0.0/16, 10.2.0.0/16, 10.3.0.0/16, 192.168.0.0/24
## Access

- Windows clients can access VNet1, VNet2, and VNet3, but routes to VNet2 and VNet3 will have to be manually added.
- Non-Windows clients can access VNet1, VNet2, and VNet3

---