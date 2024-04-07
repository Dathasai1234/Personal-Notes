---
title: AZ-140
date: 2024-04-07
resources: 
tags:
---
# Az-140
## Architecture

- Desktop and Application virtualization service.
- Works across devices with apps that you can access remote desktops and apps.

![[Pasted image 20240407174234.png]]

- The application endpoints are in customers on-premises network.
- Using **ExpressRoute**, on-premises network is extended to Azure Cloud.
- **Microsoft Entra Connect** integrates the customer's Active Directory to Microsoft Entra ID.
- To increase the capacity, customer uses **two Azure subscriptions** in a hub-spoke architecture, and connects them via virtual network peering.

---
## Components of AVD's

### Components Microsoft manages

**Web access** - This is a feature of Windows Virtual Desktop which allows you to access VD's and remote applications through any HTML-5 compatible web browser from any where on any device. You can secure the web access with MFA authentication in Microsoft Entra ID.

**Gateway** - The remote Connection Gateway service establish connection between remote users and AVD apps and desktops from any internet connected device. The client connects to the Gateway, which then orchestrates a connection from a VM back to the same gateway.

**Connection Broker** - This provides the load balancing and reconnections to existing sessions (manage user connections to VD's apps and desktop).

**Diagnostics** - This is an event-based aggregator that marks user or administrator action on the AVD deployment as success or failure, Administrator can query the event aggregator to identify failing components.

**Extensibility components** - You can manage AVD's using Windows powershell and even with Rest APIs, which also enable support for 3rd party tools.

### Components we manage

**Azure Virtual Network** - Connecting AVD host pools to AD domain, You can define network topology to access VD's and virtual apps from the intranet or internet.

**Entra ID**

**AD DS** - AVD VM's must domain-join an AD DS service. We can use Entra ID connect to associate AD DS with Entra ID.

**AVD session host** - A Host pool can run these set of OS
- Windows 10 and 11 Enterprise.
- Windows 10 Enterprise Multi-session.
- Windows server 2012 R2 and above.

- Each session host has an *AVD host agent*, which registers the VM as part of AVD workspace or tenant.
- Each host pools can have one or more *app groups*, which are collections of remote applications or desktop sessions that users can access.
- **AVD workspaces** - a management layer to manage and publish host pool resources.

---
## Host Pools

- Collection of one or more identical virtual machine within AVD environment.
- Each host pool can contain an **app group**.
- The users get access to the host pool by being allocated to that host pool using an **assigned Application Group**

### Pooled

This is for several users to sign-in and share a VM.

None of these users are local administrators of the polled VM. With pooled, you can use one of the recommended images which includes windows 10 Enterprise multisession, which is exclusive to AVD.

Users don't come to the same session host each time they connect and have limited ability to customize the desktop environment and don't usually have administrator access.

![[Pasted image 20240407193233.png | 300]]

A pooled desktop solutions assign users that session host which is currently available depending on load balancing algorithm
### Personal (persistent desktop)

This is where each individual user has their own dedicated VM.

Each user is a local administrator of the accessed VM. A user can install or uninstall applications without impacting other users.

![[Pasted image 20240407193518.png | 300]]

Allows users to always connect to the same specific session host.

---
## Azure limitations for AVD

| **Azure Virtual Desktop object** | **Per Parent container object**  | **Service limit** |
| -------------------------------- | -------------------------------- | ----------------- |
| **Workspace**                    | Microsoft Entra tenant           | 1300              |
| **HostPool**                     | Workspace                        | 400               |
| **Application group**            | Microsoft Entra tenant           | 500               |
| **RemoteApp**                    | Application group                | 500               |
| **Role assignment**              | Any Azure Virtual Desktop object | 200               |
| **Session host**                 | HostPool                         | 10,000            |
If you require more than 500 application groups, you can submit a support ticket.

- It is recommended that you deploy no more than 5000 VM's per subscription per region (applies for both pooled and personal host pools).
- You can increase the resources of multi-session host pool to accommodate more user sessions.