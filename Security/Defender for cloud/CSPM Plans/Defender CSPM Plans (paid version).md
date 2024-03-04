---
title: CSPM Plans
date: 2024-02-20
resources: 
tags:
---

# Defender CSPM Plans(paid version)

## Governance Rules

	> Environment settings > Governance rules

- You can define rules that *assign an owner* and *add a due date* for Remediating a recommendation
- Governance rules drive accountability and you are providing an SLA as you are adding a due date for a recommendation to be remediated.

- You don't have to assign a stuff to an owner and add due dates individually for every recommendation.
- Using this feature, you will save your time and efficiency and secondly, reduce the errors because you define this automation once and then you can be sure that it is working correctly in the background all the time.

- **Grace period** - if the recommendation which is assigned to an owner should be remediated in a week, till then, the secure score will be not effected. This feature is for the organizations who need some time to remediate the recommendation and dont want to impact the secure score till the grace period is crossed

![[Pasted image 20240209124221.png]]

![[Pasted image 20240131155257.png]]

We can have multiple Governance rules with same conditions. So priority comes into play to choose which Governance rules to play around.

![[20240209-0705-36.7561215.mp4]]

![[Pasted image 20240209124509.png]]

---
## Regulatory Compliance Standards

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
## Cloud Security Explorer

- Cloud security Explorer is a very nice feature but not as capable as KQL.
- Cloud security explorer allows you to query resources and logs Without the need for writing KQL queries
- You can query all resources connected to Defender for Cloud.
- KQL still has more capabilities but the barrier to use cloud security Explorer is way lower
- You can also find Query templates to use.

---
## Attack Path Analysis

- Visualizes exploitable attack paths in your environment, e.g.:
	- VM containing critical vulnerabilities is exposed to the internet
	- VM containing critical vulnerabilities is exposed to the internet with read Permissions to a key vault
	- Azure Blob storage with sensitive data is publicly accessible

- This one actually visualizes certain exploitable attack paths.

![[Pasted image 20240209105904.png]]

![[Pasted image 20240209110211.png]]

![[Pasted image 20240209110427.png]]

---
## Agentless Scanning for VMs

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
## Agentless Discovery for Kubernetes

- API-based discovery of your Kubernetes clusters, their Configurations, and deployments
- Allows you to get an idea of your Kubernetes cluster configuration and its security posture.

---
## Container Registry Vulnerability Assessment

- Container Vulnerability Assessment is powered by MDVM (Microsoft Defender Vulnerability Management)
- Scans the Azure Container Registry (ACR) and identifies vulnerabilities
- Also included in Defender for Containers

---
## DevSecOps on Azure DevOps

![[Pasted image 20240131170944.png | 700]] 

![[Pasted image 20240302104238.png]]