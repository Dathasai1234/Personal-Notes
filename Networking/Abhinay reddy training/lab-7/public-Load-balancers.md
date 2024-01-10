---
title: lab-7
date: 2023-12-13
resources: 
tags:
---
# Architecture

![[arc-public-load-balancer]]

---

pre requisites

1. created a *virtual network*
2. 3 VM’s in one *Availability set*
3. inside VM
	1. ![[Pasted image 20231218184818.png | 700]]
	2. Go to **manage** > **Add roles and Features** > Next > **Install web server (IIS)** > next > install
	3. Go to **Tools** > **Internet Information Service Manager**
	4. modified HTML page.
4. Created a **public Load balancer**
5. Created a backend pool
6. Add the vm’s to the *backend-pool*
7. created a Health probe
8. In the health probe, the *interval* is used as a <u>wait time in seconds</u> for sending a *message* to the VM for the health acknowledgement.
9. The *Un-healthy threshold* is the number of times the *message* to be sent if any unexpected occurs to the VM.
10. configure the load balancer to connect the backend pool to the frontend configuration.
11. As the load balancer is used to route *HTTP* traffic. configure the port number 80 in load balancer rule.

- The public ip address of VM will be the same as public ip of Load balancer. It doesn’t mean the public ip of vms are de-allocated.

# load-balancer

## Add front-end configuration

|                                      |     |
| ------------------------------------ | --- |
| ![[Pasted image 20231218192128.png]] | ![[Pasted image 20231218192149.png]]    |

---
## create a back-end pool and attach the VM’s to it.

![[Pasted image 20231218192324.png]]

---

## Add a health probe

|                                      |                                      |     |
| ------------------------------------ | ------------------------------------ | --- |
| ![[Pasted image 20231218192410.png]] | ![[Pasted image 20231218192424.png]] |     |
 
---

## Add load-balancer rules

![[Pasted image 20231218192703.png]]

---