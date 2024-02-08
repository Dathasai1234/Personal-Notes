---
title: Udemy
date: 2024-01-30
resources: 
tags:
---

# Index

- [[#Introduction|Introduction]]
	- [[#Introduction#CSPM Vs CWPP|CSPM Vs CWPP]]
	- [[#Introduction#Azure Policy|Azure Policy]]
		- [[#Azure Policy#Effects in Policy|Effects in Policy]]
	- [[#Introduction#ARC|ARC]]
	- [[#Introduction#KQL Query Development Process|KQL Query Development Process]]
	- [[#Introduction#Log Analytics Dedicated Cluster|Log Analytics Dedicated Cluster]]
- [[#CSPM|CSPM]]
- [[#CSPM Plans|CSPM Plans]]
	- [[#CSPM Plans#Foundational CSPM|Foundational CSPM]]
		- [[#Foundational CSPM#Inventory|Inventory]]
		- [[#Foundational CSPM#Security Recommendations|Security Recommendations]]
		- [[#Foundational CSPM#Secure Score|Secure Score]]
		- [[#Foundational CSPM#Workbooks|Workbooks]]
		- [[#Foundational CSPM#Data Exporting|Data Exporting]]
		- [[#Foundational CSPM#Remediations|Remediations]]
		- [[#Foundational CSPM#Microsoft Cloud Security Benchmark|Microsoft Cloud Security Benchmark]]
	- [[#CSPM Plans#Defender CSPM (paid version)|Defender CSPM (paid version)]]
		- [[#Defender CSPM (paid version)#Governance Rules|Governance Rules]]
		- [[#Defender CSPM (paid version)#Regulatory Compliance Standards|Regulatory Compliance Standards]]
		- [[#Defender CSPM (paid version)#Cloud Security Explorer|Cloud Security Explorer]]
		- [[#Defender CSPM (paid version)#Attack Path Analysis|Attack Path Analysis]]
		- [[#Defender CSPM (paid version)#Agentless Scanning for VMs|Agentless Scanning for VMs]]
		- [[#Defender CSPM (paid version)#Agentless Discovery for Kubernetes|Agentless Discovery for Kubernetes]]
		- [[#Defender CSPM (paid version)#Container Registry Vulnerability Assessment|Container Registry Vulnerability Assessment]]
		- [[#Defender CSPM (paid version)#DevSecOps on Azure DevOps|DevSecOps on Azure DevOps]]
- [[#CWP|CWP]]
- [[#Tasks|Tasks]]
- [[#CWP Features|CWP Features]]

# Introduction

- CNAP solution - Cloud Native Application Protection.

![[Pasted image 20240130201331.png]]

- Scan the repos of github in *DevSecOps*.
- Misconfigs in the code.
- Misconfigs of vms
<br>
- *CSPM* gives the recommendations in a proactive way and preventative way before anything bad happens.
<br>
- *CWPP* deals with runtime protection for various resources and deals with actual threats, such as:
	- App Service
	- Databases
	- DB
	- Storage
	- Containers
	- Key Vault
	- Resource Manager
	- APIs

- All features are ava in all the cloud platforms
- Protecting from the first line of code (devSecOps) to various resources (CWPP).

## CSPM Vs CWPP

- Ava plans of CSPM and CWPP.
- ! DNS for DNS and Defender for kubernetes, those are been deprecated.
- Plans:
- ![[Pasted image 20240131104515.png | 300]]
- Defender also comes with *RBAC* model.
- Pre-built RBAC roles for Defender for cloud.


| Role | Add/assign initiatives (including regulatory compliance standards) | Edit security policy | Enable/disable Microsoft Defender plans | Suppress alerts | Apply security recommendations for a resource | View alerts and recommendations |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Security Reader | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ |
| Security Admin | ✅ | ✅ | ✅ | ✅ | ❌ | ✅ |
| Contributor/Owner (RG Level) | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ |
| Contributor (Subscription Level) | ❌ | ❌ | ✅ | ✅ | ✅ | ✅ |
| Owner (Subscription Level) | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |

---
## Azure Policy

- Defines a desired configs of an Azure resource.
- DFC utilizes Azure Policy for all security recommendations.
- Azure Policy examples in the context of security:
	- Enforce the deployment of defender for servers for all VMS
	- Audit whether an NSG is associated with a subnet
	- Deny resource creation if vulnerabilities are identified

### Effects in Policy

- These effects are currently supportedin a policy definition:
	- AddToNetworkGroup
	- Append
	- Audit - *allows to do things but with an alert*
	- AuditlfNotExists
	- Deny - *deny the things you want to do*
	- DenyAction
	- DeploylfNotExists - *deploy the resource if certain properties are not fulfilled *
		- Eg - deploy *defender for servers* when you create a VM.
	- Disabled
	- Manual
	- Modify
	- Mutate

```cardlink
url: https://learn.microsoft.com/en-us/azure/governance/policy/concepts/effects
title: "Understand how effects work - Azure Policy"
description: "Azure Policy definitions have various effects that determine how compliance is managed and reported."
host: learn.microsoft.com
image: https://learn.microsoft.com/en-us/media/open-graph-image.png
```

- #Azure -policy is heavily tied to #ARM, works together.
- ![[Pasted image 20240131112542.png]]
- ![[Pasted image 20240131112925.png | 500]]

---
## ARC

Other Sources - [[ARC]]

- Manage VMs, Kubernetes Clusters and databases as If they run in Azure
- Creates an object in Azure That allows interaction with The Azure Resource Manager

![[Pasted image 20240131113300.png | 400]]

## KQL Query Development Process
#KQL-Query
1. Hypothesis
	- A query always begins with a hypothesis that you want to prove or disprove,
	- Such as: Is this IoC part of my logs?
2. Determine required tables
	- Determine the required tables for your query
3. Explore table schema
	- Consider the schema
4. Filter away
5. Visualize

#KQL/Kusto-Query-Language

![[Pasted image 20240131114027.png | 500]]

- All connected data sources are ingested in specific tables

![[Pasted image 20240131114100.png]]

![[Pasted image 20240131114135.png | 500]]

KQL-Important Operators

```cardlink
url: https://learn.microsoft.com/en-us/azure/data-explorer/kusto/query/kql-quick-reference#:~:text=KQL%20quick%20reference,-Article
title: "KQL quick reference - Azure Data Explorer & Real-Time Analytics"
description: "A list of useful KQL functions and their definitions with syntax examples."
host: learn.microsoft.com
image: https://learn.microsoft.com/en-us/media/open-graph-image.png
```

---
## Log Analytics Dedicated Cluster

#Log-Analytics supports a premium #dedicated-cluster option with the
Following features:
- Customer #Lockbox Double encryption of data at rest Support for Availability Zones
- Increased performance for cross-workspace queries
- Minimum commitment: 500 GB per day.

---
# CSPM

- Proactive and preventive security instead of waiting for threats
- Detailed visibility into the security state of your assets and workloads
- Hardening guidance to help you efficiently and effectively improve your Security posture

# CSPM Plans

![[Pasted image 20240131124030.png | 400]]

![[Pasted image 20240131124042.png | 400]]

![[Pasted image 20240131124203.png | 400]]


```cardlink
url: https://learn.microsoft.com/en-us/azure/defender-for-cloud/plan-defender-for-servers-select-plan#:~:text=Defender%20for%20Endpoint.-,Plan%20features,Expand%20table,-Feature
title: "Select a Defender for Servers plan - Microsoft Defender for Cloud"
description: "Select a Microsoft Defender for Servers plan in Microsoft Defender for Cloud to protect Azure, AWS, and GCP servers and on-premises machines."
host: learn.microsoft.com
image: https://learn.microsoft.com/en-us/media/open-graph-image.png
```


---
# CSPM Plans

[[Foundational CSPM Plans (Free)]]
[[Defender CSPM Plans (paid version)]]

---
# CWP

- Realtime threat protection for your workloads in Azure, multi-cloud And on-premises scenarios
- Integration with SIEM **Security information and event management** and XDR
- Available for most resource types

---
# CWP Plans

[[Defender for Servers]]
[[Defender for App Services]]
[[Defender for Storages]]
[[Defender for Key-vault]]
[[Defender for Resource Manager]]

---
# Tasks

- [x] Adoptive application control working. ✅ 2024-02-07
- [ ] Use-case AACW.
- [x] Use-case for agent and agentless in the VM's. ✅ 2024-02-07
- [ ] Exporting logs to 3 rd party (Event hub).
- [ ] Default log analytic workspace region deployment.
- [ ] Recommendations and alerts difference
- [x] Ways to enable the defender for endpoint. ✅ 2024-02-07
- [x] Onboarding the servers in defender for endpoint and defender for servers. ✅ 2024-02-07



| Task | Deadline |
| ---- | ---- |
| Log analytics workspaces are region specific as whatever resources you create will have their own specific location. (Monday) | 5-2-24 |
| CWPP plans research and more detailed PPT on entire DFC (Thursday) | 8-2-24 |
| Different ways to onboard non-Azure Windows Servers to MDE (Tuesday) | 6-2-24 |
