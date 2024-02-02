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

## Premium Plan

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

### Create a Premium Plan

- When you create a function app in the Azure portal, the Consumption plan is the default.
- ! To create a function app that runs in a Premium plan, you must explicitly create or choose an Azure Functions Premium hosting plan using one of the _Elastic Premium_ SKUs.
- The Azure portal makes it easy to create both the Premium plan and the function app at the same time.
- You can run more than one function app in the same Premium plan, but they must both run on the same operating system (Windows or Linux).

### Eliminate Cold Starts

Premium plan :
- Always ready instance
- Prewarmed instances

```cardlink
url: https://learn.microsoft.com/en-us/azure/azure-functions/functions-premium-plan?tabs=portal#:~:text=Always%20ready%20instances%20are%20a%20category%20of%20preallocated%20instances%20unaffected%20by%20scaling%2C%20and%20the%20prewarmed%20ones%20are%20a%20buffer%20as%20you%20scale%20due%20to%20HTTP%20events.
title: "Azure Functions Premium plan"
description: "Details and configuration options (virtual network, no cold start, unlimited execution duration) for the Azure Functions Premium plan."
host: learn.microsoft.com
image: https://learn.microsoft.com/en-us/media/open-graph-image.png
```

- When events trigger the app, they're first routed to the always ready instances.
- As the function becomes active due to HTTP events, other instances are warmed as a buffer.
- These buffered instances are called prewarmed instances. This buffer reduces cold start for new instances required during scale.
- ! A premium function app has two always ready instances configured, and the default of one prewarmed instance.
- You cannot change the number of pre-warmed instances using the portal, but using CLI and powershell, you can.

![Scale out graph](https://learn.microsoft.com/en-us/azure/azure-functions/media/functions-premium-plan/scale-graph.png)

---
# Supported Languages

| Language | Runtime stack | Linux | Windows | In-portal editing |
| ---- | ---- | ---- | ---- | ---- |
| C# (isolated worker Model) | .NET | ✓ | ✓ |  |
| C# (in-process model) | .NET | ✓ | ✓ |  |
| C# script | .NET | ✓ | ✓ | ✓ |
| JavaScript | Node.js | ✓ | ✓ | ✓ |
| Python | Python | ✓ |  | ✓ |
| Java | Java | ✓ | ✓ |  |
| PowerShell | PowerShell Core | ✓ | ✓ | ✓ |
| TypeScript | Node.js | ✓ | ✓ |  |
| Go/Rust/other | Custom Handlers | ✓ | ✓ |  |

---
# Creating a Function App

- A function app can be used to combine multiple functions.
- The name of the function app must be globally unique as it is used for the url.
- A runtime stack should be selected.
- All the functions in that function app will only support the selected runtime stack.
- Azure uses the storage account to hold all your function app code files.
- In the hosting session, you will choose a storage account.
- You will also select an operating system in which your function app will run.
- You may monitor your functions using *Application Insights*, which is a powerful logging and telemetry platform, which can give you a lot of operational insights of how your functions are performing in production.

## Creating a Function

- Authorization level for a function while creating
	- Function : a key to invoke this function
	- Anonymous : anyone can invoke the function on the internet
	- Admin : master key to access all the functions

### Code and Test in Portal
![[Pasted image 20240202155550.png]]

### Integration
![[Pasted image 20240202155559.png]]

---
### Running the Code

#### Url for the Function with the KEY
![[Pasted image 20240202155725.png]]

##### How to Get the KEY for Accessing the Url
![[Pasted image 20240202155940.png]]

Url - https://datha-app.azurewebsites.net/api/HttpTrigger1?name=Datha&code=Iw5ib3VH0DxAwD23Aev9b8EC4hf6_G2Ogf7fA7nzoz94AzFuPCY78w==

![[Pasted image 20240202155416.png]]

Add *name=datha&[key]*
![[Pasted image 20240202155419.png]]


---