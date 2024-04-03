---
title: CrowdStrike
date: 2024-03-17
resources: 
tags:
---

# Sensors

You can use previous version of sensor, but only those versions released in the last 180 days.

- Update schedules to automatically update to appropriate versions.
- Update throttling on slower networks.
- Sensor uninstall protection.

Using a same sensor more than 60 days is not recommended after the release.

## Version Management

- Fixed
	- Specific version number
- Automated
	- Auto - Early Adopter
	- Auto - latest
	- Auto - N1
	- Auto - N2
- Sensor version updates off
<br>
- Uninstall and maintenance protection

# Sensor for Windows Deployment

Unifies

- EDR
- Identity protection
- Threat intelligence
- Managed threat hunting all within a single, light weight sensor.

---
Can you prepare a report on CrowdStrike monitoring. I would like to understand what are the metrics which CrowdStrike is monitoring and even though we don’t get any incidents what are those metrics which tracks the changes.

---
## Things to do

1. Creating a custom destination table for the event hub data in log analytic workspace.
2. DCE
3. DCR
4. Grant DCR permissions in EventHub
5. Associate DCR to EventHub.

## Prerequisites

All resources in same region

- LAW
	- Needs to be linked to a dedicated cluster
	- Or have a commitment tire
- EventHub namespace with public network access

### Gather info

subscription ID,
resource group name,
workspace name,
workspace resource ID,
event hub instance resource ID