---
title: Presentation-2
date: 2023-12-29
resources: 
tags:
---
**7:05:20**

- Type of a virtual Network composed of 2 or more azure managed VMs which are automatically configured and deployed to a specific subnet called **GatewaySubnet**.
- These VM’s contains *routing tables* and run specific gateway services.
- You specify *gateway type* which determines how the Vnet gateway will be used and the actions that gateway takes.
- A Vnet can have 2 Vnet gateways
	- VPN gateway
	- ExpressRoute gateway
- Both of them use different gateway type.
- After you create VPN gateway, you can configure connections.

- ! Once the gateway is created, the VPN client will have to authenticate to the gateway, otherwise, any random person can connect to the gateway if they know the IP address of the gateway.
- You cannot create Policy based VPN for P2S connection.

## Connections you can create

- VPN tunnel connection between that VPN gateway and another VPN gateway (**VNet-to-VNet**).
- Cross-premises *IPsec/IKE* VPN tunnel connection between the VPN gateway and an on-premises VPN device (**Site-to-Site**).
- **Point-to-Site** VPN connection (VPN over *OpenVPN*, *IKEv2*, or *SSTP*), which lets you connect to your virtual network from a remote location, such as from a conference or from home.

- [Site-to-Site VPN connections](https://learn.microsoft.com/en-us/azure/vpn-gateway/design#s2smulti)
- [Point-to-Site VPN connections](https://learn.microsoft.com/en-us/azure/vpn-gateway/design#P2S)
- [VNet-to-VNet VPN connections](https://learn.microsoft.com/en-us/azure/vpn-gateway/design#V2V)


---

**31-12-2023**
**3:02:53**
# Gateway SKUs

- When you create a Vnet gateway, you specify the gateway SKU that you want to you.

| **VPN  <br>Gateway  <br>Generation** | **SKU** | **S2S/VNet-to-VNet  <br>Tunnels** | **P2S  <br>SSTP Connections** | **P2S  <br>IKEv2/OpenVPN Connections** | **Aggregate  <br>Throughput Benchmark** | **BGP** | **Zone-redundant** | **Supported Number of VMs in the Virtual Network** |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| **Generation1** | **Basic** | Max. 10 | Max. 128 | Not Supported | 100 Mbps | Not Supported | No | 200 |
|  | **VpnGw1** | Max. 30 | Max. 128 | Max. 250 | 650 Mbps | Supported | No | 450 |
|  | **VpnGw2** | Max. 30 | Max. 128 | Max. 500 | 1 Gbps | Supported | No | 1300 |
|  | **VpnGw3** | Max. 30 | Max. 128 | Max. 1000 | 1.25 Gbps | Supported | No | 4000 |
|  |  |  |  |  |  |  |  |  |
| **Generation1** | **VpnGw1AZ** | Max. 30 | Max. 128 | Max. 250 | 650 Mbps | Supported | Yes | 1000 |
|  | **VpnGw2AZ** | Max. 30 | Max. 128 | Max. 500 | 1 Gbps | Supported | Yes | 2000 |
|  | **VpnGw3AZ** | Max. 30 | Max. 128 | Max. 1000 | 1.25 Gbps | Supported | Yes | 5000 |
|  |  |  |  |  |  |  |  |  |
| **Generation2** | **VpnGw2** | Max. 30 | Max. 128 | Max. 500 | 1.25 Gbps | Supported | No | 685 |
|  | **VpnGw3** | Max. 30 | Max. 128 | Max. 1000 | 2.5 Gbps | Supported | No | 2240 |
|  | **VpnGw4** | Max. 100* | Max. 128 | Max. 5000 | 5 Gbps | Supported | No | 5300 |
|  | **VpnGw5** | Max. 100* | Max. 128 | Max. 10000 | 10 Gbps | Supported | No | 6700 |
|  |  |  |  |  |  |  |  |  |
| **Generation2** | **VpnGw2AZ** | Max. 30 | Max. 128 | Max. 500 | 1.25 Gbps | Supported | Yes | 2000 |
|  | **VpnGw3AZ** | Max. 30 | Max. 128 | Max. 1000 | 2.5 Gbps | Supported | Yes | 3300 |
|  | **VpnGw4AZ** | Max. 100* | Max. 128 | Max. 5000 | 5 Gbps | Supported | Yes | 4400 |
|  | **VpnGw5AZ** | Max. 100* | Max. 128 | Max. 10000 | 10 Gbps | Supported | Yes | 9000 |

![[Pasted image 20240103102624.png | 700]]

The selected SKU will decide the bandwidth between the networks and how many simultaneous connections we can have

---
# Availability Zones

[source](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways#:~:text=VPN%20gateways%20can%20be%20deployed%20in,gateways%20in%20Azure%20Availability%20Zones.)

- resiliency,
- scalability
- higher availability

physically and logically separates gateways within a region, while protecting your on-premises network connectivity to Azure from zone-level failures.

---
# Pricing

- hourly costs for the Virtual Network gateway
- The price is based on the gateway SKU.
- The cost is for the gateway itself and is in addition to the data transfer that flows through the gateway
- Cost for active-active setup is same as active-passive.

## Data transfer costs

- Egress data transfer from the Vnet gateway.
- The cost is for the gateway itself and is in addition to the data transfer that flows through the gateway
<br>
- sending traffic **to your on-premises VPN device**, It will be charged with the internet egress data transfer rate.
%%
- you'll incur charges based on the amount of data transferred out to the internet.
%%
- If you're sending traffic **between virtual networks in different regions**, the pricing is *based on the region*.
- If you're sending traffic only **between virtual networks that are in the same region**, there are *no data costs*. Traffic between VNets in the same region is *free*.
- [source](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways#:~:text=If%20you%27re%20sending,region%20is%20free.)