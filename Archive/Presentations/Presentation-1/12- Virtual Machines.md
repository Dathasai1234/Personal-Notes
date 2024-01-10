---
title: Presentation-1
date: 2023-11-14
resources: 
tags:
  - Compute
---
Manage each virtual machine as its own object
Patch, manage, care, and nurture your machines individually. Can script actions to make management easier.
Stateless / Stateful (But worry about backup!)
Deployed in a Virtual Network
No autoscaling service built-in to Virtual Machines
Scaled by deploying more virtual machines (If running the same workload, likely deploying in the same availability set or across availability zones)
Can run as single instance if workload requires it
Nodes using Availability Sets — 99.95% SLA
Nodes using Availability Zones — 99.99% SLA