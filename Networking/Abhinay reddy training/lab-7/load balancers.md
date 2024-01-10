---
title: lab-7
date: 2023-12-20
resources: 
tags:
---
# Table of contents

- [[#Notes|Notes]]
- [[#Distribution modes|Distribution modes]]
- [[#Health Probes|Health Probes]]
- [[#Links|Links]]


4 types

- Azure load balancers (Regional load balancer)
	- only for HTTP
- Application load balancers (Regional load balancer)
	- only for HTTPS
- Front door + CDN (Content Delivery Network) (Global)
	- HTTPS
- Traffic manager (Global)
	- HTTP

---

We can utilize the Application and traffic manager using **WAF**

---
# Notes

- used 5-tuple hash algorithm.
	- Source IP
	- Source Port
	- Destination IP
	- Destination Port
	- Protocol
- Does not interact with a payload
	- No SSL inspection or HTTP/HTTPS header rewrite.

# Select a Load Balancer Solution

- **Basic Load Balancers** allow:
	1. Port Forwarding
	2. Automatic Reconfiguration
	3. Health Probes
	4. Outbound connections through source network address translation (SNAT)
	5. Diagnostics through Azure Log Analytics for public-facing load balancers.
- **Standard Load Balancers** support all basic features and allow:
	1. HTTPS Health Probes
	2. Availability Zones
	3. Diagnostic through Azure Monitor, for Multidimensional Metrics
	4. High Availability (HA) Ports
	5. Outbound Rules
	6. A guaranteed SLA (99.99% for two or more virtual machines in different zones)

---
# Distribution modes

- Client IP (2-tuple) - 
	- Sessions from a client IP are handled by the same backend instance
- Client IP and Protocol (3-tuple)
	- Sessions from a client IP and protocol are handled by the same backend instance
	- ![[Pasted image 20231220132104.png]]

---
# Health Probes

- Standard SKU
	- TCP
	- HTTP
	- HTTPS
- Basic SKU
	- TCP
	- HTTP

Tests the availability of the servers in the backend pool.

---
# Links

[[public-Load-balancers]]
[[internal-load-balancers]]

---