---
title: Landing-zone
date: 2023-11-29
resources: 
tags:
  - landing-zones
---


---

> A landing zone is a concept or architecture, which helps you to get started with your cloud migrations based on best or leading practices. You start small, and you expand later – you put your apps in the right place.

- landing zone is a part of the *CAF* for azure.
- describes an environment that follows design principles.
- design principles like
	- application migration
	- application modernization
	- innovation
- [source]([AZ-104 Study Guide - What is an Azure Landing Zone? - cloud13.ch](https://www.cloud13.ch/2023/11/05/az-104-study-guide-what-is-an-azure-landing-zone/))

- As a cloud provider, we provide infrastructure to the client
- A client needs to migrate the resources from on-prem to the cloud, like - application servers.
- We need do have an architecture, using that we move the work load to the cloud.
- that infrastructure that includes all the concepts of monitoring, security, and many other services that azure provides.
<br>
- Landing zone is a Microsoft recommended service which we do in collaboration and put in-front of a customer to move the work load.
- before moving the resources to the cloud, we need to have a good architecture,
- Microsoft provides many guidelines to create architectures.
- If we create an infrastructure from the recommended guidance of Microsoft, we can achieve **high security**, **high scalable** and **cost effective**

---
# Landing zone

- As we prepare for cloud migration, we want to move workloads securely. Its also crutial to scale and innovate.
- Scalable migration starts with a landing zone.
<br>
- A landing zone is a place where you host your workloads pre provisioned through code.
- It provides all cloud services and best practices to add foundational capabilities.
- It provides a stable place for your work to run and a framework to scale.
- To provide scalability, we follow **5 principles of landing zone**
	- *networking services*.
		- which enable you to add or remove workloads without any disruption.
	- *set identity rules*.
		- so only trusted users can access the data

	addressing the first 2 principles enables you to start migrating low risk workloads.
	<br>
	- *Govern environment*.
		- can done with integrated compliant policies to ensure the workloads meet industry regulations
	- *Use security controls*.
		- to create a safe place for your workloads
	- *manage your environment*.
		- by monitoring performance and creating a resilient base for your workload.

These 5 principles can be used to create a robust landing zone that offers *increased speed*, *better security and performance* leading to faster and secure and efficient cloud migration.

---
# Fields

- *greenfield* when you are complete beginner and starting the cloud journey from the scratch.
- If you have an existing environment, this is referred to as *brownfield*
- It depends on the customer’s level to recommend same level of architecture.

---
# Foundational landing zone
- ![[Pasted image 20231129175737.png | 500]]
- This is the Microsoft recommended architecture for a client with a single subscription and we provide bare minimum resources in this architecture.
- If you have a single subscription and have a normal workload, which can be deployed in a single subscription.
- Start small and expand.
- can choose foundational level infrastructure and expand it to an enterprise level architecture.

---

# Best Practices

- maintain multiple subscriptions for *production*, *management* and *non-production*.
- intermediate root management group
	-  [source](https://rajanieshkaushikk.com/2021/08/29/azure-landing-zone-design-best-practices/#:~:text=BEST%20PRACTICE%3A%20Always,top%20level.%20For%20example.)
	- It is a best practice to have an intermediate <u>root management group</u> between *tenant root group* and other management groups and have a landing zone.
	- Organization-level governance and policies are applied at intermediate level root management group which is applicable to all its subscriptions.
	- There will be different policies at different hierarchy.
	- This way you will not alter the main root Management group at the top level.
- Azure tags
- Resource locks (apply where-ever applicable i.e : subscriptions, resource-groups, resources)
- Create resource groups for better organization of resources.

---
## what are the bare min resources we provide

### IAM and Policy

#### policy

- we can manage the security posture using policies.
- We enable audit level policies for the customers. 

#### IAM

- IAM are the RBAC rules.
- What kind of access you can give to a specific user or group.

### Cost Management

- Analyzing the costs of the created resources 

### Azure Monitor

- The resources we create in Azure have a matrix which is automatically enabled in the background.
- We can *configure Alerts* based on those matrix.

### Shared Services

#### AD

- extending on-prem AD to the Cloud.

### Networking

- connectivity between on-prem to azure.
- resources like 
	- Vnets, 
	- subnets, 
	- NSG’s, 
	- connectivity to on-prem, 
	- connectivity to the internet comes under this subscription.

### Management and Monitoring

- How are we setting monitoring the managed resources in Azure, like
	- log analytics
	- alerts

### Security Center

- default enabled
- Checking compatibility and compliance of the created infrastructure.
- Gives a compliance score
- Gives recommendations based on your security posture.
- Security Center can be enabled in standard SKU.

### Network Watcher

- When Traffic flows from source to destination, can take a look which port is open and which is closed, which port has an allow access and deny access.
- Can check the traffic coming to azure/from azure using IP’s which needs a source and destination IP and port number.

The Migration of the Application comes after the setup and can be deployed in a separate subscription landing zone called “*Application landing zone*”.

Monitoring and policies can be created again at this level to the subscription.

---
# Enterprise Landing Zone

![[Enterprise landing zone.png]]

- We create a Tenet and integrate on-prem AD to Azure AD.
- departments are created which are called *management groups*.
- Subscriptions will increase and each department have an owner who owns the subscriptions and if need of more subscriptions, That owner will be creating one.

## B

![[B.png]]

- In the *identity and access management*, owners can manage
	- MFA
	- Notifications
	- audit reports
	- cost optimization plans

## C

![[C.png]]


### Platform Landing Zone

- Three subscriptions which provides *shared services*.
	- `identity subscription`
	- `connectivity subscription`
	- `management subscription`

#### Identity subscription

![[identity sub.png]]



---
# Platform Landing Zone

- Is a subscription which provides shared services *identity, connectivity, management* to apps in application landing zones.
- these services often improves operational efficiency.
- One or more central teams manage the PLZ.
- ![[ns-arch-cust-expanded.svg]]


# On-ramps

| On-ramp | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Further guidance                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Start   | Your organization is at the beginning of the cloud adoption journey, also referred to as #greenfield, and you want to implement a new cloud environment based on best practices and proven architectural patterns.  <br>  <br>Start with the Azure landing zone conceptual architecture to understand the recommended end state.  <br>  <br>Explore each of the design areas. Understand the key themes in each area that form the considerations and decisions that you need to design and implement a landing zone that best fits your requirements. | - [What is an Azure landing zone?](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/)  <br>  <br>- [Azure landing zone design areas](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/design-areas)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Align   | Your organization has an existing environment that needs modification to align with the Azure landing zone target architecture and best practices, also referred to as #brownfield.  <br>  <br>See the transition from brownfield guidance to understand the decision points and technical approach to refactor environments and align with guidance in the ready methodology.                                                                                                                                                                         | - [Refactor a landing zone](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/refactor)  <br>  <br>- [Transition an existing Azure environment to the Azure landing zone conceptual architecture](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/enterprise-scale/transition)  <br>  <br>- [Scenario: Transition a single subscription with no management groups to the Azure landing zone conceptual architecture](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/align-scenario-single-subscription)  <br>  <br>- [Scenario: Transition management groups to the Azure landing zone conceptual architecture](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/align-scenario-multiple-management-groups)  <br>  <br>- [Scenario: Transition a regional organization environment to the Azure landing zone conceptual architecture](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/align-scenario-regional-org)  <br>  <br>- [Scenario: Transition an environment by duplicating a landing zone management group](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/landing-zone/align-approach-duplicate-brownfield-audit-only) |
| Enhance | Your environment is already in line with best practices, but your organization wants to add more controls or features.  <br>  <br>Explore articles that describe considerations to enhance key ongoing processes for cloud environments, such as management, governance, and security.                                                                                                                                                                                                                                                                  | - [Improve landing zone operations](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/considerations/landing-zone-operations)  <br>  <br>- [Improve landing zone governance](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/considerations/landing-zone-governance)  <br>  <br>- [Improve landing zone security](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/considerations/landing-zone-security)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |

---