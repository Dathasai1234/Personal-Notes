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

- [x] Adoptive application control working. ✅ 2024-02-07
- [ ] Use-case AACW.
- [x] Use-case for agent and agentless in the VM's. ✅ 2024-02-07
- [ ] Exporting logs to 3rd party (Event hub).
- [ ] Default log analytic workspace region deployment.
- [ ] Recommendations and alerts difference
- [ ] Governance rules.
- [x] Ways to enable the defender for endpoint. ✅ 2024-02-07
- [x] Onboarding the servers in defender for endpoint and defender for servers. ✅ 2024-02-07


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
- ![[Pasted image 20240206223515.png]]
- On-boarding script not working in windows 2016 server
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
## Log Analytic Workspace

The agent will be collecting information and sending it to the workspace. If you are Using Azure Defender for Server, you have up to *500 MB* per day per node, and after that, Log Analytics Charges will apply.

---
## Adaptive Network Hardening

> [!note] 
> Improve your network security posture with adaptive network hardening

- Adaptive network hardening provides recommendations to further harden the NSG rules.
- Adaptive Network Hardening recommendations Should be applied on internet facing virtual machines
- **Machine learning algorithm:** This makes the system "smart" and able to learn from data.
- **Actual traffic:** How devices and users interact with the network.
- **Known trusted configuration:** Approved settings for devices and connections.
- **Threat intelligence:** Information about known cyber threats.
- **Indicators of compromise:** Signs that a system might be hacked.
- **IP/port tuples:** Specific combinations of internet addresses and ports used for connections.

using all this information to understand what's normal and what's suspicious, and then recommends blocking any connections that seem risky.

 For example, let's say the existing NSG rule is to allow traffic from 140.20.30.10/24 on port 22. Based on traffic analysis, adaptive network hardening might recommend narrowing the range to allow traffic from 140.23.30.10/29, and deny all other traffic to that port. For the full list of supported ports

- **VMs are Classic VMs**: Only Azure Resource Manager VMs are supported.
- **Not enough data is available**: In order to generate accurate traffic hardening recommendations, Defender for Cloud requires at least 30 days of traffic data.
- **VM is not protected by Microsoft Defender for Servers**: Only VMs protected with *Microsoft Defender for Servers* are eligible for this feature.

1. From the **Unhealthy resources** tab, select a VM to view its alerts and the recommended hardening rules to apply.
    
    - The **Rules** tab lists the rules that adaptive network hardening recommends you add
    - The **Alerts** tab lists the alerts that were generated due to traffic, flowing to the resource, which is not within the IP range allowed in the recommended rules.

![[Pasted image 20240207154912.png]]

- The enforced rules are added to the NSG(s) protecting the VM.

**Modify rules**

- Cannot change an allow rule to become deny rule.
- You can modify the parameters of **allow** rules only.
- A **Deny all traffic** rule is the only type of "deny" rule that would be listed here, and it cannot be modified. You can, however, delete it.

**Add a new rule**

- You can add an "allow" rule that was not recommended by Defender for Cloud.
- Only "allow" rules can be added here. If you want to add "deny" rules, you can do so directly on the NSG.

**Delete a rule**

- When necessary, you can delete a recommended rule for the current session. For example, you might determine that applying a suggested rule could block legitimate traffic.

---
## File Integrity Monitor

- Examines operating system files, Windows registries, application software, and Linux system files for changes that might indicate an attack.
- Uses the *Azure Change Tracking solution* to track and identify changes in your environment.
- When FIM is enabled, you have a **Change Tracking** resource of type **Solution**.
- If you remove that resource, You are also disabling the FIM in MDC.
![[Pasted image 20240207161222.png]]
![[Pasted image 20240207161325.png]]
- The average Log Analytics data usage for a machine using Change Tracking and Inventory is approximately 40 MB per month, depending on your environment.
- The default collection frequency for Windows services is 30 minutes. You can configure the frequency using a slider on the **Windows services** tab under **Edit Settings**.
<img src = "https://learn.microsoft.com/en-us/azure/automation/change-tracking/media/overview/windowservices.png"/>
- High the frequency, might miss some changes. Setting the frequency to a smaller value allows you to catch changes that might be missed otherwise.
- For critical services, we recommend marking the **Startup** state as **Automatic**(Delayed Start) so that, once the VM reboots, the services data collection will start after the MMA agent starts instead of starting quickly as soon as the VM is up.
- ! Change Tracking and Inventory using Log Analytics agent will retire on **31 August 2024** and we recommend that you use Azure Monitoring Agent as the new supporting agent. Follow the guidelines for [migration from Change Tracking and inventory using Log Analytics to Change Tracking and inventory using Azure Monitoring Agent version](https://learn.microsoft.com/en-us/azure/automation/change-tracking/guidance-migration-log-analytics-monitoring-agent).
- *Which files should I monitor?*
	- Consider the files that are critical for your system and applications. Monitor files that you don’t expect to change without planning.
	- If you choose files that are frequently changed by applications or operating system (such as log files and text files) it will create noise, making it difficult to identify an attack.
	- [recommended items to monitor based on known attack patterns.]([Fetching Data#dizz](https://learn.microsoft.com/en-us/azure/defender-for-cloud/file-integrity-monitoring-overview#:~:text=recommended%20items%20to%20monitor%20based%20on%20known%20attack%20patterns.))

- [Enable File Integrity Monitoring (Log Analytics agent) - Microsoft Defender for Cloud | Microsoft Learn](https://learn.microsoft.com/en-us/azure/defender-for-cloud/file-integrity-monitoring-enable-log-analytics)
- [Enable File Integrity Monitoring (Azure Monitor Agent) - Microsoft Defender for Cloud | Microsoft Learn](https://learn.microsoft.com/en-us/azure/defender-for-cloud/file-integrity-monitoring-enable-ama)

---
## Adaptive Application Controls

- Enhance your security with this data-driven, intelligent automated solution that defines allowlists of known-safe applications for your machines.
- Microsoft Defender for Cloud uses machine learning to analyze the applications running on your machines and create a list of the known-safe software.
- When you enable and configure adaptive application controls, you get security alerts if any application runs other than the ones you defined as safe.

### Benefits

- Identify potential malware, even any that antimalware solutions can miss
- Improve compliance with local security policies that dictate the use of only licensed software
- Identify outdated or unsupported versions of applications
- Identify software your organization banned but is nevertheless running on your machines
- Increase oversight of apps that access sensitive data
<br>
- Defender for Cloud needs at least two weeks of data to define the unique recommendations per group of machines.

---
# Defender for App Services

![[Pasted image 20240207175809.png | 400]]

## Protects Applications Running over Azure App Service

- Attackers probe web applications to find and exploit weaknesses.
- Before being routed to specific environments, requests to applications running in Azure go through several gateways, where they're inspected and logged.
- The data is then used to identify exploits and attackers, and to learn new patterns that are used later.

### Secure

- Defender for App Service assesses the resources covered by your App Service plan and generates security recommendations based on its findings.
- Use the detailed instructions in these recommendations to harden your App Service resources.
### Detect

Defender for App Service detects a multitude of threats to your App Service resources by monitoring:

- the VM instance in which your App Service is running, and its management interface
- the requests and responses sent to and from your App Service apps
- the underlying sandboxes and VMs
- App Service internal logs

### Threats by MITRE ATT&CK Tactics

Defender for Cloud monitors for many threats to your App Service resources. The alerts cover almost the complete list of MITRE ATT&CK tactics from pre-attack to command and control.

- **Pre-attack threats** - Defender for Cloud can detect the execution of multiple types of vulnerability scanners that attackers frequently use to probe applications for weaknesses.
    
- **Initial access threats** - [Microsoft Threat Intelligence](https://go.microsoft.com/fwlink/?linkid=2128684) powers these alerts that include triggering an alert when a known malicious IP address connects to your Azure App Service FTP interface.
    
- **Execution threats** - Defender for Cloud can detect attempts to run high privilege commands, Linux commands on a Windows App Service, fileless attack behavior, digital currency mining tools, and many other suspicious and malicious code execution activities.

### Dangling DNS Detection

- [source]([Microsoft Defender for App Service - the benefits and features - Microsoft Defender for Cloud | Microsoft Learn](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-app-service-introduction))
- Subdomain takeovers are a common, high-severity threat for organizations. When a threat actor detects a dangling DNS entry, they create their own site at the destination address.
- The traffic intended for the organization’s domain is then directed to the threat actor's site, and they can use that traffic for a wide range of malicious activity.
![[Pasted image 20240207184822.png]]
[source]([Prevent subdomain takeovers with Azure DNS alias records and Azure App Service's custom domain verification | Microsoft Learn](https://learn.microsoft.com/en-us/azure/security/fundamentals/subdomain-takeover))

## All the Features of Defender for App Service.

- Protects applications running over Azure App Service
- Assesses resources covered by your App Service plan and generates security recommendations
- Monitors the VM host of your App Service and its management interface
- Monitors requests and responses sent between App Service apps
- Monitors the underlying sandboxes and VMs
- Monitors App Service internal logs
- Identifies attack methodologies applying to multiple targets
	- As a cloud-native solution, Defender for App Service can identify attack methodologies applying to multiple targets. For example, from a single host it would be difficult to identify a distributed attack from a small subset of IPs, crawling to similar endpoints on multiple hosts.
- Generates detailed, context-based, security alerts easily integrated with any SIEM
- Alerts include guidelines to help investigate and mitigate identified threats
- Regulatory compliance and industry best practices.

---
# Defender for Storages

- It helps prevent the three major impacts on your data and workload: 
	- malicious file uploads, 
	- sensitive data exfiltration, and 
	- Data corruption.
- Microsoft Defender for Storage provides comprehensive security by analyzing the *data plane* and *control plane* telemetry generated by Azure Blob Storage, Azure Files, and Azure Data Lake Storage services.
- It uses advanced threat detection capabilities powered by 
	- [Microsoft Threat Intelligence](https://go.microsoft.com/fwlink/?linkid=2128684)
	- Microsoft Defender Antivirus, and 
	- [Sensitive Data Discovery](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-data-sensitivity) to help you discover and mitigate potential threats.
- Defender for Storage includes:
	- Activity Monitoring
	- Sensitive data threat detection (preview feature, new plan only)
	- Malware Scanning (new plan only)
- ![[defender-for-storage-overview.gif]]
- You can also exclude specific storage accounts from protected subscriptions.

### Benefits

- [**Better protection against malware**](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-introduction#:~:text=Better%20protection%20against%20malware)
- [**Improved threat detection and protection of sensitive data**:](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-introduction#:~:text=Improved%20threat%20detection%20and%20protection%20of%20sensitive%20data%3A)
- [**Detection of entities without identities**](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-introduction#:~:text=Detection%20of%20entities%20without%20identities%3A)
- [**Coverage of the top cloud storage threats**](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-introduction#:~:text=Coverage%20of%20the%20top%20cloud%20storage%20threats)
- [**Comprehensive security without enabling logs**](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-introduction#:~:text=Comprehensive%20security%20without%20enabling%20logs)

## Service Working

### Activity Monitoring

- Continuously analyzes data and control plane logs from protected storage accounts when enabled.
- There's no need to turn on resource logs for security benefits.
- It also builds data models and uses statistical and machine-learning methods to spot baseline activity anomalies, which might indicate malicious behavior.
![[Pasted image 20240207194141.png]]

### Malware Scanning

- Helps protect storage accounts from malicious content by performing a full malware scan on uploaded content in near real time, applying Microsoft Defender Antivirus capabilities.
- It's designed to help fulfill security and compliance requirements to handle untrusted content.
- Every file type is scanned, and scan results are returned for every file.
- The Malware Scanning capability is an agentless SaaS solution that allows simple setup at scale, with zero maintenance, and supports automating response at scale.

### Sensitive Data Threat Protection

- [ ] [Detect threats to sensitive data - Microsoft Defender for Cloud | Microsoft Learn](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-data-sensitivity)
- Enables security teams to efficiently prioritize and examine security alerts by considering the sensitivity of the data that could be at risk, leading to better detection and preventing data breaches.
- ‘Sensitive data threat detection’ is powered by the “Sensitive Data Discovery” engine, an agentless engine that uses a smart sampling method to find resources with sensitive data.
- The service is integrated with *Microsoft Purview's sensitive information types (SITs)* and classification labels, allowing seamless inheritance of your organization's sensitivity settings.

## Pricing and Cost Controls

### Malware Scanning

- Billing per GB, monthly capping
- By default, the limit is set to 5,000 GB per month per storage account. Once this threshold is exceeded, scanning will cease for the remaining blobs, with a 20-GB confidence interval. For configuration details, refer to [configure Defender for Storage](https://learn.microsoft.com/en-us/azure/storage/common/azure-defender-storage-configure).

### Difference between Malware Scanning and Hash Reputation Analysis

#### Malware Scanning (paid Add-on Feature Available only on the New plan)

- **Malware Scanning** uses Microsoft Defender Antivirus (MDAV) to scan blobs uploaded to Blob storage, providing a comprehensive analysis that includes deep file scans and hash reputation analysis.

#### Hash Reputation Analysis (available in All plans)

- **Hash reputation analysis** detects potential malware in Blob storage and Azure Files by comparing the hash values of newly uploaded blobs/files against those of known malware by Microsoft Threat Intelligence.
- Not all file protocols and operation types are supported with this capability, leading to some operations not being monitored for potential malware uploads.

In summary, Malware Scanning, which is only available on the new plan for Blob storage, offers a more comprehensive approach to malware detection by analyzing the full content of files and incorporating hash reputation analysis in its scanning methodology.

## Enabling Defender for Storage

- Enabling Defender for Storage via a policy is recommended
- This keeps the storage accounts protected with Defender for Storage according to the organization's defined configuration.
- You can always configure specific storage accounts with custom configurations that differ from the settings configured at the subscription level (override subscription-level settings).
- [process](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-storage-policy-enablement#:~:text=subscription%2Dlevel%20settings)

## Sending Malware Scanning Results

Malware Scanning can be configured to send scanning results to the following: 

<img src = "https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/defender-for-storage-malware-scan/view-and-consume-malware-scan-results.png#lightbox"/>

**Event Grid custom topic** - for near-real time automatic response based on every scanning result. Learn more how to [configure malware scanning to send scanning events to an Event Grid custom topic](https://learn.microsoft.com/en-us/azure/storage/common/azure-defender-storage-configure?toc=%2Fazure%2Fdefender-for-cloud%2Ftoc.json&tabs=enable-storage-account#setting-up-event-grid-for-malware-scanning).  
**Log Analytics workspace** - for storing every scan result in a centralized log repository for compliance and audit. Learn more how to [configure malware scanning to send scanning results to a Log Analytics workspace](https://learn.microsoft.com/en-us/azure/storage/common/azure-defender-storage-configure?toc=%2Fazure%2Fdefender-for-cloud%2Ftoc.json&tabs=enable-storage-account#setting-up-logging-for-malware-scanning).

---
# Defender for Key-vault

The azure key vault is used to store *keys*, *Certificates* and *Secrets*

**Keys** - a file with plain string used to decrypt an encrypted information.

**Certificates** - They are used as an identity. Commonly used to represent an identity of an application to another application for may be a secure communication.

- Microsoft Defender for Key Vault detects unusual and potentially harmful attempts to access or exploit Key Vault accounts.
- ! Microsoft Defender for Key Vault is designed to help identify suspicious activity caused by stolen credentials. **Don't** dismiss the alert simply because you recognize the user or application. Contact the owner of the application or the user and verify the activity was legitimate. You can create a suppression rule to eliminate noise if necessary. Learn more in [Suppress security alerts](https://learn.microsoft.com/en-us/azure/defender-for-cloud/alerts-suppression-rules).

	- [ ] [Suppressing false positives or other unwanted security alerts - Microsoft Defender for Cloud | Microsoft Learn](https://learn.microsoft.com/en-us/azure/defender-for-cloud/alerts-suppression-rules)⏫ 

---
# Defender for Resource Manager

![[Pasted image 20240207220937.png]]

## benefits of Microsoft Defender for Resource Manager

- **Suspicious resource management operations**
- **Use of exploitation toolkits** like Microburst or PowerZure
- **Lateral movement**

---