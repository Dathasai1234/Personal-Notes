---
title: Udemy
date: 2024-01-30
resources: 
tags:
---

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
## Foundational CSPM

### Inventory

- Inventory of all Azure resources connected to Defender for Cloud
- Can be leveraged to answer questions such as:
	- Which of my subscriptions have outstanding recommendations?
	- Which of my machines with the tag 'Critical' are missing the Azure Monitor Agent?
	- Which machines in a specific resource group have a known vulnerability (using A CVE number)?

- Features:
	- Filtering the resources, based on recommendations, ...
	- Total resources
	- Unhealthy resources
	- Unmonitored resources
	- Unreg subs
	- Can add non-azure resources
	- Open Query and interact using KQL query
	- Download as CSV report
	- Recommendations for a specific resource
	- Monitoring agent installed or not
	- Defender for cloud is On or Off for a resource.

---
### Security Recommendations

- Defender for Cloud assesses your resources against security Controls in Azure, AWS and GCP
- Based on that assessment, security recommendations are provided
- Recommendations are implemented via Azure Policy

- Features
	- All recommen
	- Severity of recommendations (High, medium, low)
	- Resource health (Unhealthy, Healthy, Not applicable)
		- Unhealthy : A resource with an active recommendation
		- Healthy : A resource with no active recommendation
	- Status of the recommendation (completed or not)
	- Overdue recommendations
	- Recommendations drilling down for you resources using filters
	- Lightning bolt - Fix is available

---
### Secure Score

Entire purpose of Ss is to provide a number from 0 - 100, and this number tells you how secure you are for your various resources

![[Pasted image 20240131131940.png | 400]]

List of recomm that are associated with the MS secure score
- Features:
	- Recommendations which can increase the SS
		- Domains
			- Like enabling MFA
			- Secure Management Ports
			- Apply System Updates...
		- Have multiple recomm for a single domain
	- Max score and current score for a domain (progress bar)
	- Unhealthy resources categorized on domains

---
### Workbooks

Can also be used in Sentinel and Azure Monitor.

- Purposes - Can be used for
	- Data Visualization
	- Create Dashboards
- Workbooks allow for data visualization and dashboarding
- Workbooks can be built from scratch or customized
- Defender for Cloud includes prebuilt workbooks, such as:
	- Secure Score over Time
	- Vulnerability Assessment Findings
	- DevOps Security
	- System Updates
<br>
- Can be created from scratch or use pre-built workbooks
- Can use *KQL Query* to create dashboards and visualizations
- Also use *Add metric* option, for simplistic approach to create dashboards and visualizations using dropdowns.

![[Pasted image 20240131134232.png | 200]]

---
### Data Exporting

To export alerts and recommendations or vulnerability to other 3rd party tools.

You can stream the alerts and recommendations to the services so that the respective teams can get the expected alerts.

If you don't want to use Sentinel as a *Security information and event management (SIEM)* and want to use other SIEM solution, then you can leverage this feature of CSPM.

- ! We can Export the data to an EventHub or another log-analytic workspace
- There are built-in Azure tools for ensuring you can view your alert Data in all of the most popular solutions in use today, including:
	- Microsoft Sentinel
	- Splunk Enterprise and Splunk Cloud
	- IBM's QRadar
	- ServiceNow
	- ArcSight
	- Power Bl
	- Palo Alto Networks

- Features:
	- Export it to Event-Hub
	- Exported Date-Types
		- Which security *recomm* to export or all
		- *Recomm severity* (low, med, high)
		- *Secure score* export (all, Overall Score, Control Score)
			- Eg - only MFA Secure Score
		- Export *alerts* based on severity
		- Regulatory Compliance - ISO or Default - Azure - Sec - Benchmark
	- Frequency
		- Streaming Updates (real-time streaming)
		- Snapshots (specific snapshot).

---
### Remediations

Can be done manually and have another option which azure take cares to remediate the recomm, (when you click on Quick fix).

- Security recommendations should be remediated frequently
- Defender for Cloud always explains how to do this in general
- There is also a quick fix option available. Be careful if:
	- You manage resources with laC (you will introduce so-called *drift*)
	- You don't know the workload as you can heavily impact it by applying a fix Automatically

There will be a period called Freshness period which will tale 30 minutes to remove the recommendation after you click on *quick fix*

---
### Microsoft Cloud Security Benchmark

	Cloud Security > regulatory compliance

Renamed from
Azure Security Benchmark
⬇️
Microsoft Cloud Security Benchmark.

- Benchmark provides best practices and recommendations for your resources
- Control Domains
	- Network Security
	- Identity Management
	- Privileged Access
	- Data Protection
	- Asset Management
	- Logging and Threat Detection
	- Incident Response
	- Posture and Vulnerability Management
	- Endpoint Security
	- Backup and recovery
	- DevOps Security
	- Governance and Strategy

Lot of them are invented by Microsoft but. It also had a look at the most prominent industry benchmarks, like 

- CIS benchmarks
- NIST
- PCI
- DSS
- AWS well-Architected framework

<img src = "https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/concept-regulatory-compliance/microsoft-security-benchmark.png"/>

Microsoft took and grouped under an umbrella, which is now called Microsoft Cloud Security Benchmark.

You can leverage the benchmark to identify recomm in defender for cloud and then also to address them accordingly.

- ! These domains have all the controls and these controls have sub-controls
![[Pasted image 20240131152745.png]]

---
## Defender CSPM (paid version)

### Governance Rules

	> Environment settings > Governance rules

- You can define rules that *assign an owner* and *add a due date* for Remediating a recommendation
- Governance rules drive accountability and you are providing an SLA as you are adding a due date for a recommendation to be remediated.

- You don't have to assign a stuff to an owner and add due dates individually for every recommendation.
- Using this feature, you will save your time and efficiency and secondly, reduce the errors because you define this automation once and then you can be sure that it is working correctly in the background all the time.

![[Pasted image 20240131155257.png]]

We can have multiple Governance rules with same conditions. So priority comes into play to choose which Governance rules to play around.

---
### Regulatory Compliance Standards

- Defender for Cloud assesses your resources against popular frameworks and regulatory standards, e.g.:
	- ISO 27001
	- NIST 800-53R4
	- PCl DSS v4
	- SOC 2 Type 2
	- CIS Microsoft Azure Foundations Benchmark

It accesses your compliance and security posture based on the controls of certain frameworks.

- Features
	- Manage compliance policies
	- Check compliance offerings
	- Audio reports of all Microsoft audits
	- Download reports of your compliance based on the selected compliance framework as PFD and CVE

---
### Cloud Security Explorer

- Cloud security Explorer is a very nice feature but not as capable as KQL.
- Cloud security explorer allows you to query resources and logs Without the need for writing KQL queries
- You can query all resources connected to Defender for Cloud.
- KQL still has more capabilities but the barrier to use cloud security Explorer is way lower
- You can also find Query templates to use.

---
### Attack Path Analysis

- Visualizes exploitable attack paths in your environment, e.g.:
	- VM containing critical vulnerabilities is exposed to the internet
	- VM containing critical vulnerabilities is exposed to the internet with read Permissions to a key vault
	- Azure Blob storage with sensitive data is publicly accessible

- This one actually visualizes certain exploitable attack paths.

---
### Agentless Scanning for VMs

- Requires Defender CSPM or Defender for Servers Plan 2.
- Available for Azure, AWS, and GCP.
- Zero Performance Impact.

![[Pasted image 20240131165319.png]]

- So the vulnerability scanning is done by an agent in a Virtual machine.
- Based on the CVE id, the captured vulnerability is sent to the defender for cloud.

- *agentless scanning* is a kind of scanning which is done on a snapshot of a disk, taken to a so-called *Isolated Scanning Environment* and scanned there.
- The scanning is not done on the actual work load which does not effect the performance of the VM.
- The Vulnerability engine scans the snapshot of the disk and results of the scan are fetched out and sent to the Defender for cloud.

---
### Agentless Discovery for Kubernetes

- API-based discovery of your Kubernetes clusters, their Configurations, and deployments
- Allows you to get an idea of your Kubernetes cluster configuration and its security posture.

---
### Container Registry Vulnerability Assessment

- Container Vulnerability Assessment is powered by MDVM (Microsoft Defender Vulnerability Management)
- Scans the Azure Container Registry (ACR) and identifies vulnerabilities
- Also included in Defender for Containers

---
### DevSecOps on Azure DevOps

![[Pasted image 20240131170944.png | 700]] 

---
# CWP

- Realtime threat protection for your workloads in Azure, multi-cloud And on-premises scenarios
- Integration with SIEM **Security information and event management** and XDR
- Available for most resource types

---
# Tasks

- [ ] Adoptive application control working.
- [ ] Use-case AACW.
- [ ] Use-case for agent and agentless in the VM's.
- [ ] Exporting logs to 3rd party (Event hub).
- [ ] Default log analytic workspace region deployment.
- [ ] Recommendations and alerts difference
- [ ] Governance rules.
- [ ] Ways to enable the defender for endpoint.
- [ ] Onboarding the servers in defender for endpoint and defender for servers.
- [ ] Adoptive network hardening.

|   |   |
|---|---|
|Task|Deadline|
|Log analytics workspaces are region specific as whatever resources you create will have their own specific location.(Monday) |5-2-24|
|CWPP plans research and more detailed PPT on entire DFC(Thursday)|8-2-24|
|Different ways to onboard non-Azure Windows Servers to MDE(Tuesday)|6-2-24|

---
# Defender for Endpoint

- Defender for endpoint is Microsoft's EDR (Endpoint Detect Response) solution
![[Pasted image 20240205195116.png]]

- If we have fewer than 300 employees, then you require a defender for business license.
- You have most of the features in defender for business which are in Defender for P2.
- If you take cyber security more seriously, you require Microsoft Business Premium which is 18.10 pounds per user, per month.
- This includes
- ![[Pasted image 20240205195723.png]]
<br>
- Microsoft 365 defender is a unified place where we configure
	- Defender for cloud apps
	- Defender for office
	- Defender for endpoint
	- Defender for identity

---
# Defender for Servers

- Threat detection and advanced defenses to your windows and Linux servers
- This plan includes the integrated license for 
- Microsoft Defender for Endpoint
- vulnerability assessment scanning, 
- adaptive application controls (AAC), 
- file integrity monitoring (FIM),
- and more.
<br>
## Defender for Endpoint

- A basic flowchart explaining the Defender for Servers Plan 1/ Plan 2 integration flow:
- ![[Pasted image 20240206184411.png | 400]]
- Microsoft Defender for Servers includes an automatic, native integration with Microsoft Defender for Endpoint.
- ! The windows 2012/16 are the servers which are onboarded to MDE using Microsoft monitoring agent.
- ![[Pasted image 20240206154950.png]]
- Once the customer starts paying to the P2 plan of defender for servers, and once the data collection is installed, the MDC install the monitoring agent on the machines.
- On the workspace, the security solution is configured.
- The security solution have many features, and MDE is one of those features.
- The MDC need to create a license to the customers.
- The MDC communicated with MDE, and creates a license for the customers.
- If a license already exists for a customer. It is used.
- After the license is created, the MDC again communicates to MDE the workspaces that the customer has with the relevant security solution installed on them.
- The monitoring agent will then successfully run on the server as the license and configured by MDE.
<br>
**alert flow from server 2012, 16 > MDE > MDC**

- If any alert on the server. It first sent to MDE service, the MDE then identifies the alert that comes from the machine which is provisioned by MDC.
- That alert is forwarded to the MDC, then the alerts are available to work on it by the customer.
- The above process is only for the 2012 and 2016 servers of windows.
- In 2019 servers the MMA is not related at all.
- ! The security solution that consists MDE product doesn't work on the win 2019 and Linux.
<br>
**MDE in windows 2019**

- ! The windows servers part of 2019 does not require a monitoring agent to install MDE.
- $ The MDE is already a part of the operating system and already installed.
- All need to done is to configure the agent with customer information.
- Its called *on-boarding*, not installing. As MDE is already installed.
- ![[Pasted image 20240206162541.png]]
- The difference in 2019 servers is to get the onboarding script of MDE to onboard the server to the MDE.
- Once the extension starts running, the machine is successfully onboarded to the MDE.
- The entire licensing part and alerts flow is the same.
- The process in Linux servers is roughly same as the windows but takes an extra step to install the script.
- **Onboard package**
- ![[Pasted image 20240206214906.png]]
<br>
**unified Agent**

- The servers 2012 and 16 which should have a MMA is going to deprecate.
- These servers needs to be migrated to the unified Agent solution.
- This solution will decouples the dependency with the MMA.
- The customers having issues installing the MMA or other limitations.
- ![[Pasted image 20240206163830.png]]
1. License creation
2. Alerts integration
3. Enablement for MMA based (Windows Server 2012/2016)
4. Extension Auto Provisioning (Windows Server 2019 / Linux / Unified Solution)

```cardlink
url: https://learn.microsoft.com/en-us/azure/azure-monitor/agents/log-analytics-agent
title: "Log Analytics agent overview - Azure Monitor"
description: "This article helps you understand how to collect data and monitor computers hosted in Azure, on-premises, or other cloud environments with Log Analytics."
host: learn.microsoft.com
image: https://learn.microsoft.com/en-us/media/open-graph-image.png
```

---
## Microsoft Defender Vulnerability Management

![[Pasted image 20240206213455.png]]

- Defender Vulnerability Management delivers asset visibility, intelligent assessments, and built-in remediation tools for Windows, macOS, Linux, Android, iOS, and network devices.
- Defender Vulnerability Management rapidly and continuously prioritizes the biggest vulnerabilities on your most critical assets and provides security recommendations to mitigate risk.
- ![[Pasted image 20240206180139.png]]
- Remediate vulnerabilities and mis-configurations all in one place
- We can block vulnerable versions of applications
- You can see consolidated asset inventory.
<br>
- **browser extensions**![[Pasted image 20240206180948.png]]
- ![[Pasted image 20240206181027.png | 400]]
- **Certificates** : Can filter-out the view based on expiry-date.
- Can get the details of that certificate
- ![[Pasted image 20240206181343.png]]
- 
- Pro-actively monitor compliance against industry benchmarks.
- We can identify, assess, and remediate vulnerabilities all at one place.

---