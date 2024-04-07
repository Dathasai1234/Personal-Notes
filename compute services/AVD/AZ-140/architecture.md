---
title: AZ-140
date: 2024-04-07
resources: 
tags:
---

- Desktop and Application virtualization service.
- Works across devices with apps that you can access remote desktops and apps.

![[Pasted image 20240407174234.png]]

- The application endpoints are in customers on-premises network.
- Using **ExpressRoute**, on-premises network is extended to Azure Cloud.
- **Microsoft Entra Connect** integrates the customer's Active Directory to Microsoft Entra ID.
- To increase the capacity, customer uses **two Azure subscriptions** in a hub-spoke architecture, and connects them via virtual network peering.

