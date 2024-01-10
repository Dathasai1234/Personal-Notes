
- [[#Point-to-Site VPN|Point-to-Site VPN]]
- [[#Site-to-Site VPN|Site-to-Site VPN]]
- [[#ExpressRoute|ExpressRoute]]



allows the customers to

1. create
2. manage
3. monitor
4. and secure

connectivity between azure resources.
![[Pasted image 20231009144233.png | 500]]

![[Pasted image 20231009145552.png | 500]]

---

provide the following key network capabilities

1. Isolation and segmentation
2. Internet communications
3. communicate between azure resources
4. communicate with on-premises resources
5. Route network traffic
6. filter network traffic
7. connect virtual network.

---

- Vnet supports both **public** and **private** endpoints to enable communication between external or internal resources with other resources.
	- Public endpoints have a public ip address and can be accessed from anywhere in the world.
	- Private endpoints exist within a virtual network and have a private IP address from within the address space of that virtual network.

**Public and Private IPs:** Cloud providers typically offer both public and private IP addresses. Public IPs are used for resources that need to be accessible from the internet, such as web servers or APIs. Private IPs are used for internal communication within the cloud environment, providing a level of network isolation and security.

---

## Point-to-Site VPN

**Point-to-Site VPN:**
- This is like setting up a secure tunnel from a single computer (let's say your laptop) to your Azure network.
- Imagine you have a "magic tunnel" that lets your laptop connect to your Azure cloud as if it's sitting right there in the office.
- You configure this "magic tunnel" in your Azure settings, and then you set up your laptop to use it. Your laptop can securely access resources in your Azure network.

## Site-to-Site VPN

**Site-to-Site VPN:**
- Think of this as connecting two locations, like two offices (your physical office and your Azure cloud office).
- You have special devices, like routers or gateways, in both locations.
- You set up these devices so they can talk to each other securely over the internet, creating a "private road" between your physical office and your Azure cloud.
- This allows all the computers in your physical office to work as if they are in the Azure cloud and vice versa.

In both cases, while you won't find resources named "Point-to-Site VPN" or "Site-to-Site VPN," you'll configure these types of connections using Azure services like Virtual Network Gateways and your own VPN devices. It's like setting up secret passages (VPN connections) to access your Azure cloud from specific devices or to connect your physical office to the cloud.

## ExpressRoute

- Azure ExpressRoute provides a dedicated private connectivity to Azure that doesn't travel over the internet. ExpressRoute is useful for environments where you need greater bandwidth and even higher levels of security.

---

In summary, **ExpressRoute** is a dedicated and private connection service that provides high-speed, predictable, and low-latency access to Azure resources, while **VPNs** use encrypted tunnels over the public internet for secure access and data protection. The choice between ExpressRoute and VPN depends on your specific networking requirements and performance needs.


---

[(174) Azure Networking For Beginners | Learn Azure Networking Basics | K21Academy - YouTube](https://www.youtube.com/watch?v=feQvnIUJ3Iw)

- Machine in one network needs to communicate with another network, they need
	- route table
	- Vnet Peering