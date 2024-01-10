
In an IaaS model, the cloud provider is responsible for
- maintaining the hardware
- network connectivity
- Security

 it provides you the maximum amount of control for your cloud resources.

You’re responsible for everything else:
- operating system installation
- configuration
- maintenance
- network configuration
- database and storage configuration and so on.

![[shared-responsibility-b3829bfe.svg | 500]]

---
## Scenarios

Some common scenarios where IaaS might make sense include:

- Lift-and-shift migration: You’re standing up cloud resources similar to your on-prem datacenter, and then simply moving the things running on-prem to running on the IaaS infrastructure.
- Testing and development: You have established configurations for development and test environments that you need to rapidly replicate. You can stand up or shut down the different environments rapidly with an IaaS structure, while maintaining complete control.

---

## User Responsibilities

- **Operating System:** Users are responsible for managing and maintaining the operating system, including applying patches, updates, and configuring security settings.
- **Applications:** Users are responsible for installing, configuring, and managing their applications on the virtual machines (VMs) provided by the cloud provider.
- **Data:** Users are responsible for managing and protecting their data, including backups and data security.
- **Networking:** Users need to set up and configure networking components such as virtual networks, subnets, and firewalls.
- **Security:** Users are responsible for securing their applications and VMs, including firewall rules, intrusion detection, and identity and access management.

## Azure Responsibilities

- **Physical Infrastructure:** Azure is responsible for the physical hardware, data centers, and the virtualization layer.
- **Network Infrastructure:** Azure provides the network infrastructure and ensures network availability.
- **Storage Infrastructure:** Azure manages the storage infrastructure and ensures data durability and availability.
- **Datacenter Security:** Azure is responsible for the physical security of data centers and compliance with industry standards.

---