---
title: Presentation-2
date: 2024-01-10
resources: 
tags:
---

- In the presence of outbound configurations within a virtual network, such as a load balancer or instance-level IPs (IL PIPs), the NAT gateway takes precedence for outbound connectivity.

# Connect to Azure Services with Private Link

- Connecting from your Azure virtual network to Azure PaaS services can be done directly over the Azure backbone and bypass the internet.
- When you bypass the internet to connect to other Azure PaaS services, you free up SNAT ports and reduce the risk of SNAT port exhaustion.
- ! When you bypass the internet to connect to other Azure PaaS services, you free up SNAT ports and reduce the risk of SNAT port exhaustion.

> [!note]
> Microsoft recommends use of Azure Private Link for secure and private access to services hosted in Azure. [Service endpoints](https://learn.microsoft.com/en-us/azure/virtual-network/virtual-network-service-endpoints-overview) can also be used to connect directly to Azure PaaS services over the Azure backbone.

- A NAT gateway, load balancer and instance-level public IPs are flow direction aware and can coexist in the same virtual network to provide outbound and inbound connectivity seamlessly.