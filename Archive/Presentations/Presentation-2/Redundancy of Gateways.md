---
title: Presentation-2
date: 2024-01-16
resources: https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-highlyavailable#activestandby
tags:
---
# Index

- [[#Highly Available cross-premises|Highly Available cross-premises]]
	- [[#Highly Available cross-premises#Multiple on-premises VPN devices|Multiple on-premises VPN devices]]
	- [[#Highly Available cross-premises#Active-active VPN gateways|Active-active VPN gateways]]
	- [[#Highly Available cross-premises#Dual-redundancy: active-active VPN gateways for both Azure and on-premises networks|Dual-redundancy: active-active VPN gateways for both Azure and on-premises networks]]

# Highly Available cross-premises

To provide better availability for your cross premises connections, there are a few options available:

- Multiple on-premises VPN devices
- Active-active Azure VPN gateway
- Combination of both

---
## Multiple on-premises VPN devices

![[Pasted image 20240116155005.png]]

- You can use multiple VPN devices from your on-premises network to connect to your Azure VPN gateway.
- This configuration provides multiple active tunnels from the same Azure VPN gateway to your on-premises devices in the same location.
	1. You need to create multiple S2S VPN connections from your VPN devices to Azure. When you connect multiple VPN devices from the same on-premises network to Azure, you need to create one local network gateway for each VPN device, and one connection from your Azure VPN gateway to each local network gateway.
	2. The local network gateways corresponding to your VPN devices must have unique public IP addresses in the "GatewayIpAddress" property.
	3. BGP is required for this configuration. Each local network gateway representing a VPN device must have a unique BGP peer IP address specified in the "BgpPeerIpAddress" property.
	4. You should use BGP to advertise the same prefixes of the same on-premises network prefixes to your Azure VPN gateway, and the traffic will be forwarded through these tunnels simultaneously.
	5. You must use Equal-cost multi-path routing (ECMP).
	6. Each connection is counted against the maximum number of tunnels for your Azure VPN gateway. See the [VPN Gateway settings](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpn-gateway-settings#gwsku) page for the latest information about tunnels, connections, and throughput.

## Active-active VPN gateways

![[Pasted image 20240116155403.png]]

- each Azure gateway instance has a unique public IP address.
- each will establish an IPsec/IKE S2S VPN tunnel to your on-premises VPN device specified in your local network gateway and connection.
- Note that both VPN tunnels are actually part of the same connection.
- You'll still need to configure your on-premises VPN device to accept or establish two S2S VPN tunnels to those two Azure VPN gateway public IP addresses.
<br>
- Because the Azure gateway instances are in active-active configuration, the traffic from your Azure virtual network to your on-premises network will be routed through both tunnels simultaneously.
- even if your on-premises VPN device may favor one tunnel over the other. For a single TCP or UDP flow, Azure attempts to use the same tunnel when sending packets to your on-premises network. However, your on-premises network could use a different tunnel to send packets to Azure.

  
## Dual-redundancy: active-active VPN gateways for both Azure and on-premises networks

![[Pasted image 20240116155627.png]]

- The most reliable option is to combine the active-active gateways on both your network and Azure.
- Here you create and set up the Azure VPN gateway in an active-active configuration.
- create two local network gateways and two connections for your two on-premises VPN devices.
- The result is a full **mesh connectivity** of 4 IPsec tunnels between your Azure virtual network and your on-premises network.
<br>
- All gateways and tunnels are active from the Azure side, so the traffic is spread among all 4 tunnels simultaneously
- The primary goal of this configuration is for **high availability**
<br>
- This topology requires two local network gateways and two connections to support the pair of on-premises VPN devices.
- BGP is required to allow the two connections to the same on-premises network.