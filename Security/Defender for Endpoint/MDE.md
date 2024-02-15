---
title: Defender for Endpoint
date: 2024-02-14
resources: 
tags:
---

# Defender for Endpoint Plan 1:

- Microsoft Defender for Endpoint P1 delivers core endpoint protection capabilities such as
	- Next-generation protection
	- Manual response actions
	- Attack surface reduction capabilities
	- Attack surface reduction rules
		- Ransomware mitigation
		- Device control
		- Web protection
		- Network protection
		- Network firewall
		- Application control
	- Centralized configuration and management
		- Role-based access control
		- APIs
	- Protection for a variety of platforms
- Microsoft Defender for Endpoint P1 is available as a standalone user subscription license and as part of Microsoft 365 E3/A3/G3.

---
# Defender for Endpoint Plan 2:

- Microsoft Defender for Endpoint P2 delivers comprehensive endpoint protection capabilities including *all the capabilities of Microsoft Defender for Endpoint P1* with additional capabilities such as
	- Core Defender Vulnerability Management
	- Attack surface Reduction
	- Next-generation Protection
	- Endpoint detection And response
	- Automated investigation And remediation
	- Microsoft Threat Experts

---
- The green boxes in the following image depict what's included in Defender for Endpoint Plan 1:

![[Pasted image 20240215140934.png]]

---
# Requirements

## Licensing Requirements

[source](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/minimum-requirements?view=o365-worldwide#:~:text=Business%20requirements.-,Licensing%20requirements,-Defender%20for%20Endpoint)

- ! To onboard servers to the standalone versions of Defender for Endpoint, server licenses are required.
	- Microsoft Defender for Servers Plan 1 or Plan 2 (as part of the [Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction)) offering.
	- Microsoft Defender for Endpoint for Servers.
	- Defender for business.
		- To onboard an instance of servers you need an additional license called *Microsoft Defender for Business servers*
		- Microsoft Defender for Business servers is available as an add-on to Microsoft 365 Business Premium and the standalone version of Defender for Business.

### Difference between Microsoft **Defender for Business servers** and **Microsoft Defender for Servers Plan 1 and Plan 2**

[source](https://learn.microsoft.com/en-us/microsoft-365/security/defender-business/mdb-faq?view=o365-worldwide#what-happens-if-i-have-a-mix-of-microsoft-endpoint-security-subscriptions:~:text=What%20is%20the%20difference%20between%20Microsoft%20Defender%20for%20Business%20servers%20and%20Microsoft%20Defender%20for%20Servers%20Plan%201%20and%20Plan%202%3F)

| Microsoft Defender for Business servers | Microsoft Defender for Servers Plan 1 / Plan 2 |
| ---- | ---- |
| [Microsoft Defender for Business servers](https://learn.microsoft.com/en-us/microsoft-365/security/defender-business/get-defender-business?view=o365-worldwide#how-to-get-microsoft-defender-for-business-servers) is an add-on to Defender for Business and Microsoft 365 Business Premium only.  <br> | [Microsoft Defender for Servers Plan 1/Plan 2](https://learn.microsoft.com/en-us/azure/defender-for-cloud/plan-defender-for-servers) is an enterprise-focused offering that can be purchased with any other Microsoft cloud plan. |
| Provides a single endpoint security experience for both clients and servers within the Microsoft Defender portal ([https://security.microsoft.com](https://security.microsoft.com/)). | Part of [Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction) |
| Designed for businesses with up to 300 employees. | Includes advanced threat hunting with six months of data retention and the Microsoft Threat Experts service. |
| Enables customers who don't necessarily have a security background to set up, configure, and protect company devices, including servers. | The admin experience for Defender for Cloud resides within the Azure portal ([https://portal.azure.com](https://portal.azure.com/)). |

---
## Network and Data Storage and Configuration Requirements

- When you run the onboarding wizard for the first time, you must choose where your Microsoft Defender for Endpoint-related information is stored: in the European Union, the United Kingdom, or the United States datacenter.
- ! You cannot change your data storage location after the first-time setup.

---
## Microsoft Defender Antivirus Configuration Requirement

- Defender for Endpoint agent depends on *Microsoft Defender Antivirus (MDA)* to scan files and provide information about them.
- When *Microsoft Defender Antivirus* isn't the primary antimalware solution in your organization but Defender for Endpoint (MDE) is still used, *MDAV enters passive mode*. This mode implies a specific set of limitations compared to its active state:
- Active mode benefits:
	- Scan files.
	- Report threats.
	- Provide EDR capabilities
- Passive mode *Limitations*:
	- Real-time protection.
	- Scheduled scans.
	- EDR functionality.
		- Attack surface reduction.
		- Network protection.
- passive mode turns MDAV into a reporting and monitoring tool. It helps identify potential threats but leaves the actual mitigation and response to your chosen primary solution.

---
# MDE on non-Microsoft Products

- You'll need to confirm the Linux distributions and versions of Android, iOS, and macOS are compatible with Defender for Endpoint.
## Mac OS

- Microsoft Defender for Endpoint on macOS offers 
	- antivirus, 
	- endpoint detection and response (EDR), 
	- vulnerability management capabilities.
	For the three latest released versions of macOS. 
- Customers can deploy and manage the solution through Microsoft Intune and Jamf.

### Not Currently Supported on macOS Endpoints:

- Security Management for Microsoft Defender for Endpoint

## Linux

- Microsoft Defender for Endpoint on Linux offers 
	- antivirus (AV), 
	- endpoint detection and response (EDR), 
	- vulnerability management capabilities for Linux servers.
- Includes a full command line experience to configure and manage the agent, initiate scans, and manage threats.
- We support recent versions of the six most common Linux Server distributions: RHEL 7.2+, CentOS Linux 7.2+, Ubuntu 16 LTS, or higher LTS, SLES 12+, Debian 9+, and Oracle Linux 7.2.

### Not Currently Supported on Linux Endpoints:

- Data loss prevention
- Security Management for Microsoft Defender for Endpoint

## Android

- Running 6.0 and higher
- Web protection
	- Anti-phishing
	- Blocking of unsafe connections
- Scan for
	- Malware
	- Unwanted applications
- Additional breach prevention capabilities through integration with Microsoft Intune and Conditional Access.

## IOS

- Running ISO 11.0 and higher.
- Devises that are registered within customer's tenant are supported.
- Same Features which are provided to Android.

---
# Supported Microsoft Defender for Endpoint capabilities by platform

[source](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/supported-capabilities-by-platform?view=o365-worldwide#:~:text=Supported%20Microsoft%20Defender%20for%20Endpoint%20capabilities%20by%20platform,-Article)