---
title: Archive
date: 2024-04-16
resources: 
tags:
---

These are the updates for April.

# AI Integration.

## Security for AI. (As of Now, These Are Scoped to Azure cloud.)

- Threat protection for Gen-AI Applications.
- Security posture for Gen-AI Applications.

## ⁠AI For Security.

- Can use Co-pilot to guide through the context to understand risks in the environment.
- Assisted risk Remediation which can build the remediation steps to the recommendations.
- Risk summarization at Resource level.
	- Understand how to improve the resource security and increase security posture.

# Threat Protection

- SOC analyst can now better understand by seeing relevant cloud resource information
- Multi-Cloud Investigation

# CSPM Updates

- Risk based secure score.
	- Integrating risk prioritization with Secure Score.
- CIEM to Defender for cloud (General availability).
- Enhanced internet exposure analysis.
- CSPM for Oracle Cloud (Starting to work).
- Application centric security.
- Extend regulatory standards coverage.
- Relevant resource owner for remediations in Governance rules.

# Defender for Servers

- Qualys deprecation.
- Unified security Agent.
- Agentless malware detection.
- MDE deployment dashboard (workbook).

# Defender for Database

- Malware scanning in Azure Storage. Can scan files up to 50 GB.
- Cloud data security powered by purview & XSPM.

---
# Updates on MDE and MDB

## Product Enhancements - Experiences

- Security Settings Management, ability in defender portal where we create security policies without installing any software.

![[Pasted image 20240417002402.png]]

- Dynamic tags (Rule based tags)
	- Set and forget convenience
	- Optimized device management
	- Proactive compliance
- Unified SOC platform - Microsoft Sentinel data and capabilities now available in defender portal.

## Product Enhancements - Protection

- ### Windows Enhancements
	- Tamper Protection - unauthorized users cannot be able to change MDE settings, this is done through Anti-Virus Exclusions via Intune.
	- Performance mode now available on Windows 11 as an MDAV capability.
		- Reduces the performance impact of MDVM scans for files.
	- Dev Drive - a new form of storage volume (available in windows 11).
- ### Ransomware - Attack Disruption
	- Automatic attack disruption uses signals and uses Microsoft-based XDR response actions like:
		- Device contain.
		- Disable user.
		- Contain user.
- ### Ransomware - Deception (MDE only)
	- Immediate alerts of potential attack to security teams, allowing to respond in real-time.
	- Creates fake assets (assets as traps) like devices, users, and hosts that appears to belong to your network.
- ### Device Control
	- Device control policies in MDE.
	- Device control for macOS.
- ### Mobile threat Defense Enhancements
	- Can tag mobile devices in MDE.


## Reporting - Monthly Security Summary

- Report contains the following sections.
	- Secure score.
	- Secure score compared to other orgs.
	- Device onboarded
	- Protection against threats
	- Web content monitoring and filtering
	- Suspicious or malicious activities.

## Cross Platform Enhancements

 - Response Actions.
 - EBPF-based Sensor
 - WSL2 Plugin
 - Isolate machine API
 - Run antivirus scan API

## Geo Hosting Expansion

Now expansion is done in Australia. Can host data locally in Australia.

## Partner Enablement

- Defender Multi-tenant portal - manage tenants (50 tenants) at scale.
- Streaming API - (MDB only)