---
title: lab-6
date: 2023-11-21
resources: https://youtu.be/x7mVXIuaXN8?si=c5oqPUSRX5KYNLdf
resource_2: https://youtu.be/dsXJnDXo8ls?si=84QAWzAsJr1JULXA
tags:
  - network-lab
  - VPN
  - P2S
  - Vnet-to-Vnet
  - VPN-client
  - AD-certification
---

# Table of Contents

- [[#Architecture|Architecture]]
- [[#using **Open VPN (SSL)** protocol authentication|using **Open VPN (SSL)** protocol authentication]]
- [[#connect **VM2** and **Local machine**  using VPN Client software|connect **VM2** and **Local machine**  using VPN Client software]]
- [[#**VM3** - **LocalMachine**|**VM3** - **LocalMachine**]]
- [[#**LocalMachine** - **VM3**|**LocalMachine** - **VM3**]]

---
# Architecture

![[Pasted image 20231121200351.png | 700]]
Excalidraw - [[Lab-6]]

---
# Resource Visualizer

![[Datha-Lab-.png | 700]]

---

- Azure active directory integrated authentication
- Adding Azure VPN in **Enterprise Applications**

# AD Authentication

^24e45d

- *Tenant* - 
```copy
https://login.microsoftonline.com/30bf9f37-d550-4878-9494-1041656caf27/
```

- *Audience* - 
```copy
41b23e61-6c1e-4545-b367-cd054e0ed4b4
```

- *Issuer* - 
```
https://sts.windows.net/30bf9f37-d550-4878-9494-1041656caf27/
```

---
# Using **Open VPN (SSL)** Protocol Authentication

![[Pasted image 20231121200935.png | 700]]

---
# Connect **VM2** and **Local machine** Using VPN Client Software

![[Pasted image 20231212173309.png | 500]]

![[Pasted image 20231212173340.png | 500]]

![[Pasted image 20231121200733.png | 800]]

---
# **VM3** - **LocalMachine**

![[Pasted image 20231121195741.png | 400]]

---
# **LocalMachine** - **VM3**

![[Pasted image 20231121200152.png | 400]]

---