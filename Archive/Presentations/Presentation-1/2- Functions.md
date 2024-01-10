---
title: Presentation-1
date: 2023-11-13
resources: https://www.youtube.com/watch?v=Vxf-rOEO1q4&t=326s
tags:
  - Compute
---



- Serverless compute service that lets you run event-triggered code without having to explicitly provision or manage infrastructure
- allows you to run *small pieces of code* (**called functions**) without worrying about application infrastructure.
- extension of App service
- Supports multiple langs
	- C#
	- java
	- Js
	- Python
	- F#
	- PowerShell
	- TypeScript

|Meter|Free Grant (Per Month)|Pay as you go|
|---|---|---|
|Execution Time*|4,00,000 GB-s|$0.000016/GB-s|
|Total Executions*|1 million executions|$0.20 per million executions|

## Key Features

- **pay-per-use** pricing model
- Bring your own **dependencies** (NPM or NuGet)
- Integrated Security which is extended from App service.
- Simplified integration
	- You can combine it with external tools
- Flexible development
	- dev in **portal** or **VScode** or any other tool
	- Integration with (**GitHub, Azure DevOps, etc**).
- Open-Source

---

- Function is a piece of code.
- In order to execute that piece of code you need something called **trigger**
- A trigger is an **action** that will involve this code and will pass some basic info to this code in order to run.
- And when its done, it has some sort of output.

- Triggers always be one, but you can have **multiple inputs** and **multiple outputs**
- Everything you’re doing functions including code is stored on storage


---
## Scenarios

<iframe width="560" height="315" src="https://www.youtube.com/embed/Vxf-rOEO1q4?si=bWuQ8QBPMeDH8iGN&amp;start=225" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

- You can combine a trigger to a blob storage so that you can trigger a code whenever a new file is available on a blob and process that file and put it back on a blob storage.
- additionally you can grab some data from cosmos db and storage queue.

**parameters**
- created in which resource group
- We use some kind of expression to grab the name of the file that is being processed.
- variable that you put your contents of the file in. in this case its a stream, we’re going to put the file and all its contents in “myblob” parameter.