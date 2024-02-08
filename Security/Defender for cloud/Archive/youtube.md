---
title: Archive
date: 2024-02-08
resources: 
tags:
---

# Agenda

Microsoft Defender for Cloud Architecture
Agentless Scanning for Machines
Agentless Container Posture Management
In Defender CSPM
Cloud security graph & Attack path
Analysis
Governance Capability
Data aware security posture
Microsoft Entra Permissions Management

---
# Agentless Scanning for Machines

![[Pasted image 20240208222456.png]]

The process is to take a snapshot of the disk and mount that disk to an equivalent Operative system server. If the server is a Linux. The snapshotted disk is monitored on a VM that is Linux based.

The concept is not a 1 - 1, to create a VM for every snapshotted disk all a VM. 

**1st process**
It is going to be a multiple disk on a temporary VM that is going to be used to host those snapshots. As the disk is mounted to the VM.

**2nd process**
The second process is Microsoft Defender vulnerability Management Solution will scan these disks. 
Its going to look for all the known vulnerability

**3rd process**
Once the scan is completed which can take 30 mins to 1 hour. The actual disk and server used temporarily hold the snapshot are going to be purged.
The meta data shared back within Defender for cloud. Within one day, you should be able to have an inventory of all the vulnerabilities that were found.

> The engine that is used by the agentless scanning is our own Microsoft Defender vulnerability Management engine.

---
# Agentless Secret Scanning

Notion of scanning a VM for Secrets, creds and malware.

 What are those secrets
 1. SSH private keys.
 2. AWS access keys.
 3. AWS RDS SQL connection string.
 4. Storage account connection strings.
 5. Storage account SAS tokens.
 6. SQL connection strings.

We already got a snapshot of a VM disk and scanned by the #MDVM (Microsoft Defender Vulnerability Management) engine. Another engine set of engine also scanning the same disk for *secrets* like the above once.

The thing is not only finding the vulnerabilities for a VM, lets say using that vulnerability the attacker might exploit and have a bridge to that VM and take those secrets and laterally moving to next workload to attack and most likely to access. I