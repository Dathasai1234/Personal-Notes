---
title: Sentinel
date: 2024-02-20
resources: 
tags:
---

# Defender for Cloud and Sentinel

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

# Microsoft Sentinel Solution

- Packed integrations that deliver end-to-end product value and enable customers to easily *ingest data*, *monitor data*, *hunt*, *investigate*, *respond and connect* with different products , platforms and services
- These integrations are the collections of multiple components of Microsoft Sentinel content, such as:
![[Pasted image 20240223160255.png]]

---
# What is SIEM

[What Is SIEM? (youtube.com)](https://www.youtube.com/watch?v=9RfsRn7m7OE)

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

- The SIEM is infused with AI, ML and Analytics which will correlate all the different data in the real time.
- The SIEM outputs High-Fidelity (better alerts) Alerts and they are going to prioritize based on the priority.

---
# What is SOAR

[What is SOAR (Security, Orchestration, Automation & Response) (youtube.com)](https://www.youtube.com/watch?v=k7ju95jDxFA)
![[SOAR timeline]]

- There are two scenarios where you manually detect and respond, and automation.
- The problem is that we can do automation only for what you seen before.
- The concept of *orchestration* is the way you handle these first of the kind. We still have a human involved, but just guiding the actions but not doing every action. Another way of thinking of it, it's like semi-automated.
- The idea of SOAR is to try to move as much as we can from the manual to a more automated or orchestrated response.
- Lets assume we have a breach in a database.
- It sends an indication up to the SIEM.
- Takes the incident and give a real time alarm and sends it either within the SIEM and have it managed, or sends it up to *XDR*.
- XDR then sends a message over to the *SOAR* to open a case..
- Case is the thing that we're going to use to manage this all the way through to completion and track it along the process.
- The case is then attached with many artifacts which have all the information of compromised resources and source IP and all.
- This case is then assigned to a security analyst.
- So basically SOAR is a case management system which is detected and attach the appropriate artifacts.
- Now the analyst have the necessary info on the breach, they can do investigation and they need something to guide them along the way.
- The *playbook* is basically a set of steps where we have said, in advanced.
- We can you *dynamic playbook* for that. What you do as the second step will depend on the output of the first step.
- We can draw these playbook in a GUI.
- The SOAR system will have have a dashboard which visualize all the happenings, like we have number of tickets opened to certain number of cases, how long it takes to resolve those cases, for our further analysis.

![[SOAR working]]

---
# EDR, MDR, XDR and SIEM and SOAR.

Source - [(719) EDR, MDR & XDR Explained - YouTube](https://www.youtube.com/watch?v=z983AM8etCA)

![[Pasted image 20240223182601.png]]

## EDR

- Focus is on malicious behavior.
- It monitors activities and events on devices, looks for patterns that may indicate malicious action.
- This provides data for future investigation and this data is vital when the breach is detected.
- The EDR provides details on how the breach occurred and what the attackers actually did.
- This is the part of *Detection* part
- *Response*: can proactively take action to mitigate attacks before they have a chance to cause damage.
- If events are recorded that indicate a system has been breached, EDR can automatically isolate the system from the network in order to cut off the network.
- This is the separate solution for the AV. A lot of security vendors pack both EDR and AV in a single package.
- ! The challenge with EDR is the amount of information it produces.
- Depending on the context every data produced by an EDR system can be good or bad. It is a bit hard to detect a definitely good or definitely bad information.
- EDR provides way more alerts for investigation than a traditional AV.

## MDR

- This is a marketing term used to describe a package that consists of EDR software + managed service to take care of it for you.
- The value of an MDR solution comes down to the quality of the filtering and advice they give you.
- A good MDR service will reduce the efforts and expense required for a company to derive value from an EDR solution.

## XDR

- EDR focuses on endpoints. XDR solutions integrate data from other systems as well.
- It is an EDR solution while pull in the logs from other sources like firewalls.

## XDR Vs SIEM and SOAR

- SIEM provides a single source for your security data and provides actionable response, but doesn't provide any kind of automated remediation.
- SOAR can orchestrate and automate the common tasks and remediations.
- XDR does the same sort of things as both SIEM and SOAR.
- XDR is not so comprehensive compared either of these two tools.
- XDR is more focused on endpoints and data ingestion and analytics of XDR is not as powerful as SIEM tool.
- The orchestration capabilities are limited compared to SOAR.
- The XDR tools are cheaper.
- The SEAM and SOAR tools are expensive.