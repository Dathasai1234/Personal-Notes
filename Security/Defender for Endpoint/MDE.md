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
# Onboarding Servers to Microsoft Defender for Endpoint.

![[Pasted image 20240215170703.png]]
## Onboarding Using Local Script

- You first manually onboard individual devices to MDE.
- You might want to do this first when *testing* the service before you commit to onboarding all the devices in your network.
- This script has been optimized for use on up to ten devices.
- Local scripting is a special onboarding method for evaluating (testing) Microsoft Defender for Endpoint.
- The data reporting frequency is *higher* than with other onboarding methods when onboarding using a local script.
- Not normally used in production deployments.
- Microsoft recommends limiting the number of deployments using local scripts to *ten*.
- If you want to onboard more than 10 devices, it is recommended to use other deployment options like *Group Policy* or *Microsoft Endpoint Configuration Manager*.

- The onboarding process is straight forward for 2019 and 2022 servers as the *MDE.Windows* extention is already integrated with operating system. We just have to provision it using the onboarding script
- But in previous versions 2019 and 2012 servers needs some extra steps to onboard.
- There are some pre-requisites for the on-boarding process.
	- The servers needs to be updated (security updates).
	- Two packages *md4ws.msc* package and *on-boarding script* needs to be downloaded from the defender portal.
	- Md4ws script should be executed and then on-boarding script.
- This will now on-board the server to MDE.

![[Pasted image 20240215190259.png | 500]]


### Onboarding 2019 and 2022 servers.

- You can get the *Local Script package* from the *Microsoft Defender portal*.
- Click on `Settings > Onboarding`
- Select an operating system : The process of onboarding will change depending on the operating system you choose.
![[Pasted image 20240215171940.png]]

- Deployment model : Select *Local Script*
![[Pasted image 20240215172013.png]]

- Now you can download the Package.
- Run the Script by extracting the package in the server you want to onboard.
- You can only run the script as an administrator.
- The onboarding process will begin.
![[Pasted image 20240215181735.png]]

- You can run the cmd command to check the status of on-boarding.
- `sc query sense`
![[Pasted image 20240215172242.png]]

#### Registry Which Shows the Onboarding Status

`Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Advanced Threat Protection\Status`

##### Registry of a Machine Which is On-boarded

![[Pasted image 20240215182014.png]]

##### Registry of a Machine Which is not yet On-boarded
![[Pasted image 20240215173128.png]]

- Running the On-boarding Script will change the registry.
- It will take some time to show the on-boarded in defender endpoint portal.
- You can also offboarding using Local Script.

![[Pasted image 20240215183409.png]]

- This will change the registry properties: OnboardingState to 0.

### Onboarding 2012 and 2016 servers

- If you try to on-board directly, it will give you an error.
![[Pasted image 20240215192538.png]]



---
## Onboarding via Group Policy

