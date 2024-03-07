---
title: Udemy
date: 2024-02-08
resources: 
tags:
---

# Index

- [[#Defender for Servers|Defender for Servers]]
	- [[#Defender for Servers#Defender for Endpoint|Defender for Endpoint]]
	- [[#Defender for Servers#Defender for Endpoint Features|Defender for Endpoint Features]]
		- [[#Defender for Endpoint Features#Microsoft Defender Vulnerability Management|Microsoft Defender Vulnerability Management]]
		- [[#Defender for Endpoint Features#Log Analytic Workspace|Log Analytic Workspace]]
		- [[#Defender for Endpoint Features#Adaptive Network Hardening|Adaptive Network Hardening]]
		- [[#Defender for Endpoint Features#File Integrity Monitor|File Integrity Monitor]]
		- [[#Defender for Endpoint Features#Adaptive Application Controls|Adaptive Application Controls]]
		- [[#Defender for Endpoint Features#Benefits|Benefits]]
		- [[#Defender for Endpoint Features#Network Layer Threat Detection|Network Layer Threat Detection]]

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
- Endpoint detection and response (EDR) features that are provided by Microsoft Defender for Endpoint Plan 2.
	- [Attack surface reduction](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/overview-attack-surface-reduction)
		- Hardware isolation
		- Application control
		- Ransomware protection
		- Controlled folder access
		- Network protection
		- Web protection
		- Exploit protection
		- Device control
	- [Next-generation protection](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/next-generation-protection), including real-time scanning and protection and [Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/next-generation-protection).
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
**Alert flow from server 2012, 16 > MDE > MDC**

- If any alert on the server. It first sent to MDE service, the MDE then identifies the alert that comes from the machine which is provisioned by MDC.
- That alert is forwarded to the MDC, then the alerts are available to work on it by the customer.
- The above process is only for the 2012 and 2016 servers of windows.
- In 2019 servers the MMA is not related at all.
- ! The security solution that consists MDE product doesn't work on the win 2019 and Linux.

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

## Defender for Endpoint Features

- Defender for endpoint is Microsoft's EDR (Endpoint Detect Response) solution
![[Pasted image 20240205195116.png]]

- If we have fewer than 300 employees, then you require a defender for business license.
- You have most of the features in defender for business which are in Defender for P 2.
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
### Microsoft Defender Vulnerability Management

[source](https://www.youtube.com/watch?v=nm3l3mqwQ3w&pp=ygVJYnJlYWNoIGFuZCB0aHJlYXQgaW5zaWdodHMgaW4gTWljcm9zb2Z0IGRlZmVuZGVyIFZ1bG5lcmFiaWxpdHkgbWFuYWdlbWVudA%3D%3D)

**Definition** : MDVM helps you to discover potential impactful threats and vulnerabilities and security misconfigurations in your environment.

MDVM capabilities are included in:

#### MDVM capabilities you get in MDE plan 2

3. Defender for servers

If you have *MDE plan 2*, these are the core *MDVM* capabilities you get.

1. Device discovery
2. Device inventory
3. Vulnerability assessment
4. Configuration assessment
5. Risk based prioritization
6. Remediation tracking
7. Continuous monitoring
8. Software inventory
9. Software usages insights

*MDVM Add-on* provides these premium MDVM capabilities for *MDE Plan 2*

1. Security baselines assessment
2. Block vulnerable applications
3. Browser extensions assessment
4. Digital certificate assessment
5. Network share analysis
6. Hardware and firmware assessment
7. Authenticated scan for Windows

#### MDVM standalone license

*MDVM standalone* provides full MDVM capabilities for any EDR solution. The above *16* capabilities.

#### MDVM in Defender for servers

*DEFS plan 1 :*

1. Vulnerability assessment
2. Configuration assessment
3. Risk based prioritization
4. Remediation tracking
5. Continuous monitoring
6. Software inventory
7. Software usages insights

*DEFS plan 2 :*

All *14* capabilities of MDVM.
<br>
![[Pasted image 20240206180139.png]]

The dashboard of MDVM gives you information of **exposure score**, **Exposure distribution** and **secure score** of your environment.

A lower exposure score means devices are less vulnerable to exploitation.

The dashboard also shows top 3 recommendations, vulnerable software's and exposed devices.

You can increase the security posture by acting on MDVM recommendations.

You can increase the secure score by acting on MDVM recommendations. There are 2 icon associated to the recommendations.

The *bullseye icon* represents *breach insights* which indicates an active recommendation to an active alert in your org
![arrow hitting a target.](https://learn.microsoft.com/en-us/microsoft-365/media/defender-vulnerability-management/tvm_alert_icon.png?view=o365-worldwide) possible active alerts

The *bug icon* represents *threat insights* indicates one or more vulnerabilities are tied to this recommendations.
![red bug.](https://learn.microsoft.com/en-us/microsoft-365/media/defender-vulnerability-management/tvm_bug_icon.png?view=o365-worldwide) associated public exploits

You can request the remediation where you can directly open a ticket in Intune or service now.

You can create *exceptions* for those recommendations if you have more time to consider it. It will ask the exception scope, reason and duration.

You can keep track of MDVM remediations and exceptions in *remediation* tab which is integrated to intune and service now. This tab shows continuous updates and progress of your remediation activity. You can see all the exception you have created in exception tab.

- ! There is a 180 day retention period for completed remediation activities. To keep the Remediation page performing optimally, the remediation activity will be removed 6 months after its completion.

You can also examine *weaknesses* using MDVM. The weaknesses page have all the known vulnerabilities. You can filter out them and remediate.

- ! You also have visibility on software usage in your organization of past 30 days. 
- This information is critical when it comes to find software's with vulnerabilities in your organizations. These insights help orgs to block vulnerable applications.

You can open the software page by clicking a software from the inventory for more information on it. You can know the number of devices in which that software is used, and in those devices, you get an exposure score in a graph view, and number of vulnerabilities in that software wrt severity.

---

- Remediate vulnerabilities and mis-configurations all in one place
- We can block vulnerable versions of applications
- You can see consolidated asset inventory.
- **browser extensions** : Shows all the extensions used in the organization. Also shows the permissions you have granted to the extensions and use them or add restrictions to use those extensions which are not safe to use. All the extension management is done in a centralized way.
- **Certificates** : Can filter-out the view based on expiry-date.
	- Can get the details of that certificate
- Pro-actively monitor compliance against industry benchmarks.
- We can identify, assess, and remediate vulnerabilities all at one place.

---
### Log Analytic Workspace

The agent will be collecting information and sending it to the workspace. If you are Using Azure Defender for Server, you have up to *500 MB* per day per node, and after that, Log Analytics Charges will apply.

---
### Adaptive Network Hardening

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

Using all this information to understand what's normal and what's suspicious, and then recommends blocking any connections that seem risky.

 For example, let's say the existing NSG rule is to allow traffic from 140.20.30.10/24 on port 22. Based on traffic analysis, adaptive network hardening might recommend narrowing the range to allow traffic from 140.23.30.10/29, and deny all other traffic to that port. For the full list of supported ports

- **VMs are Classic VMs**: Only Azure Resource Manager VMs are supported.
- **Not enough data is available**: In order to generate accurate traffic hardening recommendations, Defender for Cloud requires at least 30 days of traffic data.
- **VM is not protected by Microsoft Defender for Servers**: Only VMs protected with *Microsoft Defender for Servers* are eligible for this feature.

1. From the **Unhealthy resources** tab, select a VM to view its alerts and the recommended hardening rules to apply.
    
    - The **Rules** tab lists the rules that adaptive network hardening recommends you add
    - The **Alerts** tab lists the alerts that were generated due to traffic, flowing to the resource, which is not within the IP range allowed in the recommended rules.

![[Pasted image 20240207154912.png]]

- The enforced rules are added to the NSG (s) protecting the VM.

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
### File Integrity Monitor

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
### Adaptive Application Controls

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
### Network Layer Threat Detection

Some network configurations restrict MDC to generate alerts on suspicious network activity.

For Defender for Cloud to generate network alerts, ensure that:

- Your virtual machine has a public IP address (or is on a load balancer with a public IP address).
- Your virtual machine's network egress traffic isn't blocked by an external IDS solution.

---