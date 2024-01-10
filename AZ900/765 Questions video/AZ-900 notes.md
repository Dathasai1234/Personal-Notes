---
title: 765 Questions video
date: 2023-12-11
resources: https://www.youtube.com/watch?v=C6RFbx1STUk
tags:
---
# Table of contents

- [[#Intro of AZ900|Intro of AZ900]]
- [[#SaaS, PaaS, IaaS|SaaS, PaaS, IaaS]]
- [[#PowerShell script|PowerShell script]]
- [[#Traffic managing|Traffic managing]]

# Keywords

1. ADDS
2. managed domain services [source](https://www.google.com/search?q=what+is+managed+domain+in+azure&ie=UTF-8#:~:text=Azure%20Active%20Directory%20Domain%20Services%20(Azure%20AD%20DS)%2C%20part%20of%20Microsoft%20Entra%2C%20enables%20you%20to%20use%20managed%20domain%20services%E2%80%94such%20as%20Windows%20Domain%20Join%2C%20group%20policy%2C%20LDAP%2C%20and%20Kerberos%20authentication%E2%80%94without%20having%20to%20deploy%2C%20manage%2C%20or%20patch%20domain%20controllers.)
3. Federation services
4. managed services

# Intro of AZ900

![[Pasted image 20231211184203.png | 500]]

---

1. Which of the following is a correct statement?

- Private Cloud = Public Cloud + Hybrid Cloud
- Public Cloud = Hybrid Cloud + Private Cloud
- $ Hybrid Cloud = Private Cloud + Public Cloud

---
2. Which of the following describes a benefit of cloud services?

- $ Economies of scale
- Fixed workloads
- Unpredictable costs.

Economies of scale is the ability to do things more cheaply and more efficiently when operating at a larger scale in comparison to operating at a smaller scale.

---

3. When you implement a SaaS (Software as a Service) solution, you are responsible for?

- Installing patches on Operating Systems
- Configure High Availability
- $ Configuring the SaaS solution
- Install SaaS solution

---

#Agility: Cloud agility is the ability to quickly develop, test, and launch applications in a cloud-based environment.

#Fault_tolerance: It is the ability of a system to continue to function in the event of a failure of some of its components.

#High_availability: It means to keeps services up and running for long periods of time, with little downtime, depending on the service in question.

---

4. Which cloud model provides the <u>greatest degree of ownership</u> and control?

a) Hybrid Cloud
b) **Private Cloud**
c) Public Cloud

---

5. Which cloud model provides the<u> greatest degree of flexibility</u>?

a) **Hybrid Cloud**
b) Private Cloud
c) Public Cloud

---

6. Which of the following describes a public cloud?

a) Is owned and operated by the organization that uses the resources from that cloud.
b) Let organizations run applications in the cloud or on-premises.
**c)** Provides resources and services to multiple organizations and users, who connect through a secure
network connection.

---

7. You have legacy applications that require specialized mainframe hardware, and you have newer shared applications. Which cloud deployment model would be best for you?
a) Hybrid Cloud
b) Private Cloud
c) Public Cloud

---
# SaaS, PaaS, IaaS

![[Pasted image 20231211193132.png | 500]]

---

# PowerShell script
![[Pasted image 20231211193807.png | 500]]

---

# Traffic managing

Your Azure environment contains multiple Azure virtual machines. You need to ensure that a virtual machine named VM1 is accessible from the Internet over HTTP.


|Action|Required|Description|
|---|---|---|
|Modify a network security group (NSG)|True|Use NSG to filter network traffic between Azure resources in an Azure virtual network. A network security group contains security rules that allow or deny inbound network traffic to, or outbound network traffic from, several types of Azure resources.|
|Modify a DDoS protection plan|False|DDoS is a form of attack on a network resource. DDoS protection plan is used to protect against DDoS attacks. It has nothing to with accessibility of Virtual machine over HTTP.|
|Modify an Azure firewall|False|Azure Firewall is a cloud-native and intelligent network firewall security service that provides the best of breed threat protection for your cloud workloads running in Azure.|
|Modify an Azure Traffic Manager profile|False|Azure Traffic Manager is a DNS-based load balancing solution.|

---

You can create Group Policies in Azure Active Directory (Azure AD).

True
**False**

---

- You cannot create Group policies in Azure Active Directory
- You can Join Windows 10 devices to Azure Active Dir <u>except Home editions</u>
- You cannot join Android devices to Azure AD

---

Your company plans to migrate all its data and resources to Azure. The company's migration plan
states that only Platform as a Service (PaaS) solutions must be used in Azure. You need to deploy an Azure
environment that meets the company's migration plan. What should you create?

a) An azure virtual machines, Azure SQL databases, and Azure Storage accounts.
b) An Azure App Service and Azure virtual machines that have Microsoft SQL Server installed.
**c)** An Azure App Service and Azure SQL databases.
d) An Azure storage accounts and web server in Azure virtual machines.

---

- ! **ADDS** is a part of **Microsoft Entra**
- 