---
title: Policies
date: 2023-11-07
resources: https://medium.com/@cloud.devops.enthusiast/azure-policy-942253b46a59
resource_2: https://youtu.be/4wGns611G4w
tags:
  - governance
---
# Table of contents

- [[#RBAC vs policy|RBAC vs policy]]
- [[#Types of policies|Types of policies]]
- [[#policy assignment|policy assignment]]
- [[#Policy enforcement|Policy enforcement]]
- [[#exclusions (not scope)|exclusions (not scope)]]
- [[#policy limits|policy limits]]
- [[#Blueprints|Blueprints]]

---

- **denial effect** (not allowed a resource to be created if not compliant).
- **audit effect** (allowed a resource to be created with a warning message).
	- shows non compliant resources in ==> *compliance **/** policy name **/** activity logs*.

# RBAC vs policy

| RBAC                                                                                              | Policy                                                                                                       |
| ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Controlling the permissions, the actions that I can take on certain scopes and certain resources. | Those guard rails to control the types of resources we can use, type of configurations we’re allowed to have | 

---

---

- ! Question
- How can i use azure policy to really enforce those requirements we have?

---

- Arc enabled Infrastructure. what it does is, it takes the azure control plane and takes it to other clouds, it takes it on premises.
- There are aspects of it that will also apply to these arc enabled resources.
- so don't think of this as only azure resources because <mark style="background: #FF5582A6;">arc enablement extends that azure control plane elsewhere, all these azure policies gonna apply there as well</mark>.

- so when i think about azure policy it is a <mark style="background: #FF5582A6;">json format</mark> and the goal is i'm going to create this structure so i'm going to think about.
- this json document and i can do many different types of things i might say hey 
	- i want to restrict to certain locations, 
	- i want certain tag values, 
	- i only want to use this type of skew 
	there's a whole set of different things i can do

---

policies

1. Properties

2. definition location

3. parameters

4. Policy rule

![[Pasted image 20231107122420.png | 500]]
- allof - &
- anyOf - ||
- not - !

- if condition
- then effect
	- disabled (will not evaluated)
	- append/modify (adding to an array / add, replace, remove tags or properties)
	- deny (based on the condition, deny it)
	- audit (let it happen, track the compliance)
	- audit if not exist
	- deploy if not exist (execute a template, to perform some remediation to make something right)

# Types of policies

1. built-in
2. custom
3. static

---
# policy assignment

assigning that particular policy to a level of hierarchy and that policy can be inherited to the lower levels.

---
# Policy enforcement

1. enabled
2. disabled

- think of disabled as *what-if* mode.

---
# exclusions (not scope)

exclude that policy to a particular
- sub
- res grp
- res

---

# policy limits


<mark style="background: #FF5582A6;">exclusions limit</mark> - **400 exclusions**

<mark style="background: #FF5582A6;">definitions</mark>- an *entry of Scope*
	management group or
	subscription. 
	
<mark style="background: #FF5582A6;">assignments and exemptions</mark>- an *entry of Scope*
	management group,
	subscription, 
	resource group, or 
	individual resource.

![[Screenshot 2023-11-07 132804.png | 500]]

|Object type|Maximum count|Scope|
|---|---|---|
|Policy definitions|500|Management group or subscription|
|Initiative definitions|200|Management group, subscription, or tenant|
|Policy or initiative assignments|200|Management group, subscription, resource group, or individual resource|
|Exemptions|1000|Management group, subscription, resource group, or individual resource|
|Policy definition parameters|20|Policy definition|
|Initiative definition policies|1000|Initiative definition|
|Initiative definition parameters|400|Initiative definition|
|Policy or initiative assignment exclusions (notScopes)|400|Policy or initiative assignment|
|Policy rule nested conditionals|512|Policy rule|
|Remediation task resources|50,000|Policy definition, initiative, or assignment request body|
|Request body size (bytes)|1,048,576|Policy definition, initiative, or assignment request body|

---
# Blueprints

Blueprints used to combine resource groups and arm templates and RBAC and policies

---
