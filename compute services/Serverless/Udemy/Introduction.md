---
title: Udemy
date: 2024-02-01
resources: 
tags:
---

> [!note] 
> Serverless is "**Service not Servers**"
# What is Serverless

- Still is Platform-as-a-Service (PAAS), but "more"
- You really don't know or care what the hardware is that runs the app
- You don't have to take steps to scale
- Azure Functions, Azure Logic Apps, Azure Bots, Machine Learning
- Integrating with Azure Storage and Azure Databases via API
- Serverless are event driven
- Don't have applications that are always running, no concept of "continuous"
- Requires as *event* for something to happen, even a timer.
- Sub-second billing (consumption)
- If your app never run, you don't get charged
<br>
- Key things to remember that the code *should be small*
- So instead of having monolithic applications, you have a lot of little applications that have a single purpose.
- Since a function is only doing one thing, the code is small.
- Small code is easier to create, easier to manage, less prone to bugs
- Some functions can be 15 lines of code 
- Develop in the cloud

![[Pasted image 20240201134902.png]]

---
## Azure's Serverless Features

**Compute** - Azure Functions
**Storages** - Blobs, tables, Queues, and files
**Data** - Cosmos DB, including SQL, MongoDB, table and Gremlin.
<br>
**Security** - Azure Entra ID
**Messaging** - Event grid, and Service Bus
**Workflow** - Logic Apps
<br>
**API Management** - including Function Proxies
**Analytics** - Stream analytics, and Event Hubs
**Intelligence** - Bot Service, and Cognitive services

---
# Logic Apps

