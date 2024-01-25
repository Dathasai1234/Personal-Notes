---
title: Training - 4
date: 2024-01-25
resources: 
tags:
---
[![](https://attack.mitre.org/theme/images/mitre_attack_logo.png)](https://attack.mitre.org/)
# Reconnaissance

- *Gather info* they can use to plan future operations
- techniques that involve active or passive gathering info that can be used to support targeting.
- info includes details of the victim like
	- org
	- infrastructure
	- staff/personnel

---
# Resource Development

- Adversary trying to *establish resources* they can use to support operations.
- techniques that involve creating, purchasing, or compromising/stealing resources that can be used to support targeting.
- Such resources include infrastructure, accounts, or capabilities.

---
# Initial Access

- The adversary is trying to *get into your network*.
- exploiting weaknesses on public-facing web servers.
- Footholds gained through initial access may allow for continued access, like valid accounts and use of external remote services, or may be limited-use due to changing passwords.

---
# Execution

- The adversary is trying to *run malicious code*.
- adversary-controlled code running on a local or remote system.
- Techniques that run malicious code are often paired with techniques from all other tactics to achieve broader goals, like exploring a network or stealing data.
- For example, an adversary might use a remote access tool to run a PowerShell script that does <u>Remote System Discovery</u>[^1].

- [^1]: In Remote System Discovery, the adversary might be interested in obtaining information such as:
	- **System Names and IP Addresses:** Identifying what systems are present on the network.
	- **System Configuration:** Gathering details about the configuration of remote systems, including operating system version, installed software, and system settings.
	    
1. **Network Topology:** Understanding how systems are interconnected within the network.