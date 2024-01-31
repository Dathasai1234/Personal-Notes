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
- ![[Pasted image 20240131104515.png]]
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
- ![[Pasted image 20240131112925.png]]

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

![[Pasted image 20240131114027.png | 400]]

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

|Feature|Details|Plan 1|Plan 2|
|---|---|---|---|
|**Defender for Endpoint integration**|Defender for Servers integrates with Defender for Endpoint and protects servers with all the features, including:  <br>  <br>- [Attack surface reduction](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/overview-attack-surface-reduction) to lower the risk of attack.  <br>  <br>- [Next-generation protection](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/next-generation-protection), including real-time scanning and protection and [Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/next-generation-protection).  <br>  <br>- EDR, including [threat analytics](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/threat-analytics), [automated investigation and response](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/automated-investigations), [advanced hunting](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/advanced-hunting-overview), and [Endpoint Attack Notifications](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/endpoint-attack-notifications).  <br>  <br>- Vulnerability assessment and mitigation provided by [Microsoft Defender Vulnerability Management (MDVM)](https://learn.microsoft.com/en-us/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management-capabilities) as part of the Defender for Endpoint integration. With Plan 2, you can get premium MDVM features, provided by the [MDVM add-on](https://learn.microsoft.com/en-us/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management-capabilities#vulnerability-managment-capabilities-for-servers).|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**Licensing**|Defender for Servers covers licensing for Defender for Endpoint. Licensing is charged per hour instead of per seat, lowering costs by protecting virtual machines only when they're in use.|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**Defender for Endpoint provisioning**|Defender for Servers automatically provisions the Defender for Endpoint sensor on every supported machine that's connected to Defender for Cloud.|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**Unified view**|Alerts from Defender for Endpoint appear in the Defender for Cloud portal. You can get detailed information in the Defender for Endpoint portal.|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**Threat detection for OS-level (agent-based)**|Defender for Servers and Defender for Endpoint detect threats at the OS level, including virtual machine behavioral detections and _fileless attack detection_, which generates detailed security alerts that accelerate alert triage, correlation, and downstream response time.  <br>  <br>[Learn more about alerts for Windows machines](https://learn.microsoft.com/en-us/azure/defender-for-cloud/alerts-reference#alerts-windows)  <br>  <br>[Learn more about alerts for Linux machines](https://learn.microsoft.com/en-us/azure/defender-for-cloud/alerts-reference#alerts-linux)  <br>  <br>  <br>[Learn more about alerts for DNS](https://learn.microsoft.com/en-us/azure/defender-for-cloud/alerts-reference#alerts-dns)|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)  <br>[Provided by MDE](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**Threat detection for network-level (agentless security alerts)**|Defender for Servers detects threats that are directed at the control plane on the network, including network-based security alerts for Azure virtual machines. [Learn more](https://learn.microsoft.com/en-us/azure/defender-for-cloud/alerts-reference)|❌|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**Microsoft Defender Vulnerability Management (MDVM) Add-on**|Enhance your vulnerability management program consolidated asset inventories, security baselines assessments, application block feature, and more. [Learn more](https://learn.microsoft.com/en-us/azure/defender-for-cloud/deploy-vulnerability-assessment-defender-vulnerability-management).|❌|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**Security Policy and Regulatory Compliance**|Customize a security policy for your subscription and also compare the configuration of your resources with requirements in industry standards, regulations, and benchmarks. Learn more about [regulatory compliance](https://learn.microsoft.com/en-us/azure/defender-for-cloud/regulatory-compliance-dashboard) and [security policies](https://learn.microsoft.com/en-us/azure/defender-for-cloud/security-policy-concept)|❌|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**[Qualys vulnerability assessment](https://learn.microsoft.com/en-us/azure/defender-for-cloud/deploy-vulnerability-assessment-vm)**|As an alternative to Defender Vulnerability Management, Defender for Cloud can deploy a Qualys scanner and display the findings. You don't need a Qualys license or account.|❌|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**[Adaptive application controls](https://learn.microsoft.com/en-us/azure/defender-for-cloud/adaptive-application-controls)**|Adaptive application controls define allowlists of known safe applications for machines. To use this feature, Defender for Cloud must be enabled on the subscription.|❌|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**Free data ingestion (500 MB) to Log Analytics workspaces**|Free data ingestion is available for [specific data types](https://learn.microsoft.com/en-us/azure/defender-for-cloud/faq-defender-for-servers#what-data-types-are-included-in-the-daily-allowance-) to Log Analytics workspaces. Data ingestion is calculated per node, per reported workspace, and per day. It's available for every workspace that has a _Security_ or _AntiMalware_ solution installed.|❌|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**Free Azure Update Manager Remediation for Arc machines**|[Azure Update Manager remediation of unhealthy resources and recommendations](https://learn.microsoft.com/en-us/azure/update-center/update-manager-faq#im-a-defender-for-server-customer-and-use-update-recommendations-powered-by-azure-update-manager-namely-periodic-assessment-should-be-enabled-on-your-machines-and-system-updates-should-be-installed-on-your-machines-would-i-be-charged-for-azure-update-manager) is available at no additional cost for Arc enabled machines.|❌|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**[Just-in-time virtual machine access](https://learn.microsoft.com/en-us/azure/defender-for-cloud/just-in-time-access-overview)**|Just-in-time virtual machine access locks down machine ports to reduce the attack surface. To use this feature, Defender for Cloud must be enabled on the subscription.|❌|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**[Adaptive network hardening](https://learn.microsoft.com/en-us/azure/defender-for-cloud/adaptive-network-hardening)**|Network hardening filters traffic to and from resources by using network security groups (NSGs) to improve your network security posture. Further improve security by hardening the NSG rules based on actual traffic patterns. To use this feature, Defender for Cloud must be enabled on the subscription.|❌|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**[File integrity monitoring](https://learn.microsoft.com/en-us/azure/defender-for-cloud/file-integrity-monitoring-overview)**|File integrity monitoring examines files and registries for changes that might indicate an attack. A comparison method is used to determine whether suspicious modifications have been made to files.|❌|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|**[Docker host hardening](https://learn.microsoft.com/en-us/azure/defender-for-cloud/harden-docker-hosts)**|Assesses containers hosted on Linux machines running Docker containers, and then compares them with the Center for Internet Security (CIS) Docker Benchmark.|❌|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
|[Network map](https://learn.microsoft.com/en-us/azure/defender-for-cloud/protect-network-resources)|Provides a geographical view of recommendations for hardening your network resources.|❌|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|
| [Agentless scanning](https://learn.microsoft.com/en-us/azure/defender-for-cloud/concept-agentless-data-collection) |Scans Azure virtual machines by using cloud APIs to collect data.|❌|![](https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/icons/yes-icon.png)|


```cardlink
url: https://learn.microsoft.com/en-us/azure/defender-for-cloud/plan-defender-for-servers-select-plan#:~:text=Defender%20for%20Endpoint.-,Plan%20features,Expand%20table,-Feature
title: "Select a Defender for Servers plan - Microsoft Defender for Cloud"
description: "Select a Microsoft Defender for Servers plan in Microsoft Defender for Cloud to protect Azure, AWS, and GCP servers and on-premises machines."
host: learn.microsoft.com
image: https://learn.microsoft.com/en-us/media/open-graph-image.png
```


---
## Foundational CSPM

### Features

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

Microsoft took and grouped under an umbrella, which is now called Microsoft Cloud Security Benchmark.

You can leverage the benchmark to identify recomm in defender for cloud and then also to address them accordingly.

- ! These domains have all the controls and these controls have sub-controls
![[Pasted image 20240131152745.png | 1000]]

---
## Defender CSPM (paid version)

### Governance Rules

	> Environment settings > Governance rules

- You can define rules that *assign an owner* and *add a due date* for Remediating a recommendation
- Governance rules drive accountability and you are providing an SLA as you are adding a due date for a recommendation to be remediated.

- You don't have to assign a stuff to an owner and add due dates individually for every recommendation.
- Using this feature, you will save your time and efficiency and secondly, reduce the errors because you define this automation once and then you can be sure that it is working correctly in the background all the time.

![[Pasted image 20240131155257.png | 1000]]

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