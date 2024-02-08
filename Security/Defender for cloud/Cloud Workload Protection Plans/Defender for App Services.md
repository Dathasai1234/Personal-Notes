---
title: Cloud Workload Protection Plans
date: 2024-02-08
resources: 
tags:
---

# Index

- [[#Defender for App Services|Defender for App Services]]
	- [[#Defender for App Services#Protects Applications Running over Azure App Service|Protects Applications Running over Azure App Service]]
		- [[#Protects Applications Running over Azure App Service#Secure|Secure]]
		- [[#Protects Applications Running over Azure App Service#Detect|Detect]]
		- [[#Protects Applications Running over Azure App Service#Threats by MITRE ATT&CK Tactics|Threats by MITRE ATT&CK Tactics]]
		- [[#Protects Applications Running over Azure App Service#Dangling DNS Detection|Dangling DNS Detection]]
	- [[#Defender for App Services#All the Features of Defender for App Service.|All the Features of Defender for App Service.]]

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
