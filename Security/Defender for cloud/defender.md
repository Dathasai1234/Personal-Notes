---
title: Defender for cloud
date: 2024-01-29
resources: 
tags:
---
- ! cloud-native application protection platform
- designed to protect cloud-based application from cyber threats and vulnerabilities.
<br>
- Defender have two segments
	- A development security operations (*DevSecOps*) solution that unifies security management at the code level across multicloud and multiple-pipeline environments
	- A cloud security posture management (*CSPM*) solution that surfaces actions that you can take to prevent breaches
	- A cloud workload protection platform (*CWPP*) with specific protections for servers, containers, storage, databases, and other workloads

- Microsoft 365 Defender provides an overview of attacks, including suspicious and malicious events that occur in cloud environments.

- **Services in Defender**
	- Security Posture.
	- Workload Protection.
	- Inventory.
	- Recommendations.
	- Regulatory compliance.

- **pricing**
	- *Basic* - Foundational CSPM
		- Basic security features and recommendations
		- ![[Pasted image 20240129155233.png | 400]]
	- *Defender CSPM*
		- To increase the features and recommendations and there is a price to pay.
		- ![[Pasted image 20240129155202.png | 400]]

- **Azure Security Benchmark**
	- It is an initiative with many policies that get applied to the subscriptions.
	- The recommendations of defender comes from this initiative which have all of the policies applied to your subscription.
	- ![[Pasted image 20240129152959.png]]

- **Regulatory compliance**
	- The security posture of the resources are compared against the policies under #Azure-security-benchmark.

## Vulnerability Assessment

![[Pasted image 20240129161225.png]]

![[Pasted image 20240129161435.png]]

## Just in time VM Access

- Opening RDP port 3389 is not the best practice. When it comes to hosting infrastructure in the cloud, you always pay attention to reduce the surface area attack in your infrastructure.
- Key things to remember to open fewer management ports open.
- Just in time feature access works with your Network Security Groups.
- You can also control the duration of VM access using Just in time VM access.
- The Just in time feature is applied only when VM is connected to any form of NSG. Not when it is stopped or NSG is disassociated.
- A new rule will be created in Your NSG named as "securitycenter..."
- You can also see or apply the feature from defender from cloud.