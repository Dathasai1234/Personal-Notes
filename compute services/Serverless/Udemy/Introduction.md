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
# Functions

## Usecase

- Convert an *XML* file to *json* format.
![[Pasted image 20240201202314.png]]

- Upload image, resize to thumbnail, extract objects present in the image and save it in database
- Notify admin of upload
![[Pasted image 20240201202545.png]]

---
# Triggers and Bindings

## Triggers

- Trigger is what making a function to run.
- Each Azure Function has exactly one trigger.
- Common types:
	- HTTP
	- Timer
	- Blob storage
	- Queue...

## Bindings

- Bindings is a way of connecting services/resources with azure functions
- Binding types:
	- Input Binding
	- Output Binding
- A function can have multiple input or output bindings and no input/output bindings.
- Triggers and bindings reduces boiler plate code.

### Helpful Sources

```cardlink
url: https://learn.microsoft.com/en-us/azure/azure-functions/functions-triggers-bindings?tabs=isolated-process%2Cpython-v2&pivots=programming-language-csharp#supported-bindings
title: "Triggers and bindings in Azure Functions"
description: "Learn to use triggers and bindings to connect your Azure Function to online events and cloud-based services."
host: learn.microsoft.com
image: https://learn.microsoft.com/en-us/media/open-graph-image.png
```

---
# Pricing

```cardlink
url: https://learn.microsoft.com/en-us/azure/azure-functions/functions-premium-plan?tabs=portal
title: "Azure Functions Premium plan"
description: "Details and configuration options (virtual network, no cold start, unlimited execution duration) for the Azure Functions Premium plan."
host: learn.microsoft.com
image: https://learn.microsoft.com/en-us/media/open-graph-image.png
```

- Consumption
- Premium
- App Service

## Consumption

|Meter|Free Grant (Per Month)|Pay as you go|
|---|---|---|
|Execution Time*|4,00,000 GB-s|$0.000016/GB-s|
|Total Executions*|1 million executions|$0.20 per million executions|

- Serverless plan
- Scales automatically
- Charged for what you use.
- Billing
	- ! Based on Number of executions
	- Execution time
	- Memory used
	- Free quota per month

## Premium plan

|Meter|Pay as you go|1 year savings plan|3 year savings plan|
|---|---|---|---|
|vCPU duration|vCPU: $0.173 vCPU/hour|vCPU: $0.14359 vCPU/hour  <br>~17% savings|vCPU: $0.14359 vCPU/hour  <br>~17% savings|
|Memory duration|Memory: $0.0123 GB/hour|Memory: $0.010209 GB/hour  <br>~17% savings|Memory: $0.010209 GB/hour  <br>~17% savings|

- Warm instances to avoid #cold_start
	- In azure, when your function is not called for few minutes, that function instance is removed from the memory.
	- When the function is called in the future, that instance is initialized and loaded into the memory which might take some time resulting a cold or delayed start.
	- This happens in consumption plan.
	- In premium plan, an instance is always running which is called #warm_instance
- Avoid cold starts with warm instances.
- Virtual network connectivity.
- Supports [longer runtime durations](https://learn.microsoft.com/en-us/azure/azure-functions/functions-premium-plan?tabs=portal#longer-run-duration).
- [Choice of Premium instance sizes](https://learn.microsoft.com/en-us/azure/azure-functions/functions-premium-plan?tabs=portal#available-instance-skus).
- More predictable pricing, compared with the Consumption plan.
- High-density app allocation for plans with multiple function apps.
<br>
- ! Billing is done based on number of core seconds and memory allocated across instances.
- $ No execution charge
- Source : 
```cardlink
url: https://learn.microsoft.com/en-us/azure/azure-functions/functions-premium-plan?tabs=portal#:~:text=Billing%20for%20the,pricing%20page.
title: "Azure Functions Premium plan"
description: "Details and configuration options (virtual network, no cold start, unlimited execution duration) for the Azure Functions Premium plan."
host: learn.microsoft.com
image: https://learn.microsoft.com/en-us/media/open-graph-image.png
```
- ! Every premium plan has at least one active (billed) instance at all times.

### Create a premium plan

- When you create a function app in the Azure portal, the Consumption plan is the default.
- ! To create a function app that runs in a Premium plan, you must explicitly create or choose an Azure Functions Premium hosting plan using one of the _Elastic Premium_ SKUs.
- The Azure portal makes it easy to create both the Premium plan and the function app at the same time.
- You can run more than one function app in the same Premium plan, but they must both run on the same operating system (Windows or Linux).

### Eliminate cold starts

