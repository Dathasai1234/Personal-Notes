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
 [source]( https://learn.microsoft.com/en-us/azure/defender-for-cloud/secret-scanning#:~:text=By%20using%20agentless%20secrets%20scanning%2C%20you%20can%20proactively%20discover%20the%20following%20types%20of%20secrets%20across%20your%20environments%20 (in%20 Azure%2 C%20 AWS%20 and%20 GCP%20 cloud%20 providers)%3A)

Defender for Cloud's agentless secrets scanning for Virtual Machines (VM) locates plaintext secrets that exist in your environment

We already got a snapshot of a VM disk and scanned by the #MDVM (Microsoft Defender Vulnerability Management) engine. This engine also scans the same disk for *secrets* like the above once.

The thing is not only finding the vulnerabilities for a VM, lets say using that vulnerability the attacker might exploit and have a bridge to that VM and take those secrets and laterally moving to next workload to attack and most likely to access.

![[Pasted image 20240208232921.png]]

Secrets findings can be found using the *Cloud Security Explorer* and the *Secrets* tab with their metadata like secrets type, file name, file path, last access time, and more.

You can also find the secret findings in the asset inventory, select a VM and open the secrets tab.

The agentless scanner verifies whether SSH private keys can be used to move laterally in your network. Keys that aren't successfully verified are categorized as `unverified` on the Recommendations page.

You can remediate the secret findings from *attack path analysis*, you can also use *cloud security explorer* and use pre-designed templates as shown in the above screenshot.