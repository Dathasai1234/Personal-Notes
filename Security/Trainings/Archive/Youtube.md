---
title: Archive
date: 2024-01-25
resources: 
tags:
---

# How Hackers Move Through Networks (with Ligolo)
 [![](https://www.youtube.com/watch?v=qou7shRlX_s)](https://www.youtube.com/ "YouTube Home")
- technique is called the *lateral movement*. Moving from one device to another.
- Ethical hackers do have to move from one network to whole another network.
- If the penetration tester compromise the website or any publicly accessible service like email server. They usually land in a zone called #DMZ zone. Called as *Demilitarized Zone* network.
- Servers in the #DMZ zone can be accessible from public internet, but the organization local network cannot be accessible.
- So the DMZ computers act as the boundary between the local network and outer internet.
- These DMZ servers are the only servers which can communicate with internal resources of organization.
- Hackers use this as an advantage and use a technique called #Pivoiting.
- Tools like Chisels and ProxyChains help for pivoiting and *logolo-ng* written in GOLANG language.
- [logolo-ng]([Pivoting through network with ease! (4pfsec.com)](https://4pfsec.com/ligolo))
- Ligolo-ng is a simple, lightweight and fast tool that allows pentesters to establish tunnels from a reverse TCP/TLS connection using a tun interface.