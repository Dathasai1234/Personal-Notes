---
title: Presentation-1
date: 2023-11-14
resources: 
tags:
  - Compute
---
Containers orchestrated by Kubernetes
Typically Stateless or Externalised State
Multiple pods running across Virtual Machines
Master Control Plane is public
Workload endpoints are private by default unless exposed by Load Balancer or Proxy
Worker nodes are Single Tenant, Control Plane managed by Microsoft
Kubernetes can be deployed on other platforms, AKS is a native service
Node autoscale functionality is in preview (currently!), can scale pods
Deployed into a virtual network
Worker nodes using Availability Sets — 99.95% SLA
Worker nodes using Availability Zones — 99.99% SLA

<iframe width="560" height="315" src="https://www.youtube.com/embed/-o5OWSbeNbs?si=om0XCHKDj26SROqW&amp;start=296" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

---

<iframe width="560" height="315" src="https://www.youtube.com/embed/o5qkgsyfRao?si=FESNRw9Yh1pern14" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

**Master** controls the cluster and the nodes in it
**Nodes** host the containers inside them, Containers are inside separate PODS
**PODS** are logical collection of containers which need to interact with each other for an Application
**Replication Controller** is Master's resource to ensure that requested no of Pods are running on nodes always
**Service** is an object on Master that provides had balancing across a replicated group of Pods