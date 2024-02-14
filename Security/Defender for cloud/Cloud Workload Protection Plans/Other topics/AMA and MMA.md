---
title: Other topics
date: 2024-02-14
resources: 
tags:
  - Azure_Monitoring_Agent
  - Microsoft_Monitoring_Agent
---
![[Pasted image 20240214163411.png]]

- The purpose of AMA is to collect logs from guest operating system and ingest them to *log analytic workspace*.
- The servers can be exist anywhere, either in Azure, on-prem or hybrid cloud.
- As you ingest the logs in log analytic workspace, you can use other services like sentinel, performance monitoring in Azure monitor and MDC.
- ! The Azure monitoring agent is not the only agent for collecting logs. It is designed to eliminate the limitations of *Microsoft Monitoring Agent also called as Log Analytic Agent/MMA*
- Older versions of windows servers were using MMA to onboard the server to MDE before unified client is introduced.
- So as the MMA is in the deprecation process and we need a plan to migrate from MMA to AMA.
![[Pasted image 20240214165802.png]]

## Why should you migrate to AMA

### 1. Usage of WorkspaceID and Workspacekey.

- The 1st challenge is the enablement of the agent itself.
- Whenever the agent is installed, it needs the WorkspaceID and Workspacekey to communicate with the workspace, and you need a method to secure these.
- The agent has to present it's identity before it can ingest Data to the workspace
![[Pasted image 20240214170439.png]]

- These credentials are available in agents section of the workspace and visible to everyone which is a security concern.

### 2. Configuration Was defined at Workspace.

![[Pasted image 20240214170636.png]]

- The configuration in the sense the logs to be collected is configured at workspace level but not to the agent.
![[Pasted image 20240214170833.png]]

- The real challenge is when another server is connected to the same workspace using the same WorkspaceID and Workspacekey, the same set of log collection configuration is set to it.
- This challenge is resolved in AMA.

### AMA working

![[Pasted image 20240214171150.png]]

- AMA uses *Managed Identity* which eliminates the dependency on the WorkspaceID and Workspacekey.
- The configuration is now changed to *data collection rules* which are now added directly to the agent level.

#### Data collection rules

![[Pasted image 20240214171800.png]]

### 3. No transformation Was available, which Results in high data Ingestion cost

- No Transformation was available; the data will get ingested as it is