
- [[#Physical Infrastructures|Physical Infrastructures]]
- [[#Regions|Regions]]
- [[#Availability Zones|Availability Zones]]
- [[#Region pairs|Region pairs]]


Throughout your journey with Microsoft Azure, you’ll hear and use terms like 
1. Regions, 
2. Availability Zones, 
3. Resources, 
4. Subscriptions, and more.

The core architectural components of Azure may be broken down into two main groupings:
1. the physical infrastructure, and the 
2. management infrastructure.

## Physical Infrastructures

They’re facilities with resources arranged in racks, with dedicated power, cooling, and networking infrastructure.

individual datacenters aren’t directly accessible. Datacenters are grouped into *Azure Regions* or *Azure Availability Zones* that are designed to help you achieve **resiliency** and **reliability** for your business-critical workloads.

## Regions

region is a **geological area** on the planet that contains at least one, but potentially multiple datacenters that are nearby and networked together with *low-latency network*.

Azure intelligently assigns and controls the resources within each region to ensure workloads are appropriately balanced.

- When you deploy a resource in Azure, you'll often need to choose the region where you want your resource deployed.

## Availability Zones

**physically separate datacenters** within an Azure region.

- Each availability zone is made up of one or more datacenters equipped with independent power, cooling, and networking.
- An availability zone is set up to be an **isolation boundary**.
- If one zone goes down, the other continues working.
- Availability zones are connected through
	- high speed
	- private fiber-optic networks.

<mark style="background: #FF5582A6;">Important</mark>

- ! To ensure resiliency, a minimum of three separate availability zones are present in all availability zone-enabled regions. However, not all Azure Regions currently support availability zones.

![[Pasted image 20231005124003.png]]

---
## Region pairs

![[Pasted image 20231005132414.png | 500]]

<mark style="background: #FF5582A6;">Important</mark>

- ! Not all Azure services automatically replicate data or automatically fall back from a failed region to cross-replicate to another enabled region. In these scenarios, recovery and replication must be configured by the customer.

Because the pair of regions are directly connected and far enough apart to be isolated from regional disasters, you can use them to provide reliable services and data redundancy.

---

![[Pasted image 20231113145925.png | 800]]

![[Pasted image 20231113134620.png | 800]]