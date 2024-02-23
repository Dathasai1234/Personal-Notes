---
title: Sentinel
date: 2024-02-20
resources: 
tags:
---

# Defender for cloud and Sentinel

- Defender for cloud :
	- Used for protection and governance of azure and hybrid workloads.
- Sentinel :
	- Sentinel is a #SIEM and #SOAR solution of Microsoft.
	- **SIEM** is basically a data aggregator where you can collect data from all the sources including on-premises and other cloud providers and analyze it using *threat intelligence* and *advances analytics*.
	- It uses AI for *Threat intelligence*.
	- It is also a **SOAR** solution allows to automate and orchestrate common tasks and workloads using built-in or custom *playbooks*.
	- You can also integrate Sentinel with multiple services like *Service now* which is a tool for automations like automated remediation, Unified view of incidents
- Sentinel is a cloud native SIEM and SOAR
	- Security Information and Event Management.
	- Security Orchestration Automation and Response.
- You can improve your security posture by ==collection of the data==, ==detection of undetected threats==, ==Investigate== and ==respond==.
- Sentinel supports #Lighthouse :
	- Lighthouse is a multitenant management service which lets a service provider use his own tenant to manage the subscriptions and resource groups that are delegated by the customer.

# Microsoft Sentinel solution

- Packed integrations that deliver end-to-end product value and enable customers to easily *ingest data*, *monitor data*, *hunt*, *investigate*, *respond and connect* with different products , platforms and services
- These integrations are the collections of multiple components of Microsoft Sentinel content, such as:
![[Pasted image 20240223160255.png]]

---
# What is SIEM

- SIEM - Security Information and Event Management.
- Hackers need one blind spot and use that vulnerability to exploit.
- The Security analysts always deal with disconnected tools, 100s of tools which are not communicating with each other. So they're going back and forth, checking all these different tools, which creates 100s if not 1000s alerts daily.
- SIEM is the solution which provides *High-Fidelity Alerts*.
- The SIEM is a tool which pulls in sources all the places.
- Aggregates the data,
- Consolidates the data,
- Sorts and Prioritizes to identify threats.

## Inputs to SIEM

- Logs
- Threat intel
- Vulnerability feeds
- Network Detection and Response (NDR)
- Endpoint Detection and Response (EDR)

- The SIEM is infused with AI, ML and Analytics which will corelate all the different data in the real time.
- The SIEM outputs High-Fidelity (better alerts) Alerts and they are going to protitise based on the priority.

---
# What is SOAR

