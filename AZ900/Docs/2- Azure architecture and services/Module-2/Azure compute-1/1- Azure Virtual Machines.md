
- VMs provide **infrastructure as a service (IaaS)** in the form of a virtualized server and can be used in many ways.

- Just like a physical computer, you can customize all of the software running on your VM. VMs are an ideal choice when you need:
	- Total control over the operating system (OS).
	- The ability to run custom software.
	- To use custom hosting configurations.

- An Azure VM gives you the flexibility of virtualization without having to buy and maintain the physical hardware that runs the VM.
- As an **IaaS** offering, you still need to configure, update, and maintain the software that runs on the VM.

---
## Scale VMs in Azure

- You can run single VMs for testing, development, or minor tasks.
- Or you can group VMs together to provide high *availability*, *scalability*, and *redundancy*.
- Azure can also manage the grouping of VMs for you with features such as *scale sets* and *availability sets*.

---
### Virtual machine **scale sets**

- ! Scale sets allow you to centrally *manage*, *configure*, and *update* a large number of **VMs** in minutes.
- The number of VM instances can automatically increase or decrease in response to demand
- you can set it to scale based on a defined schedule.
- Virtual machine scale sets also automatically deploy a **load balancer** to make sure that your resources are being used efficiently.

---
### Virtual machine **availability sets**

- ! Tool to help you build a more resilient, highly availability environment.
- Availability sets are designed to ensure that VM’s **stagger updates**, and have **varied power and network connectivity**, preventing you from losing all your VMs with a single network or power failure.
- Availability sets do this by grouping VM’s in *2 ways*
	1. Update Domain
	2. Fault Domain

#### Update Domain

- distributes VMs across multiple update domains. An update domain is a logical group that ensures that not all VMs in an Availability Set are updated or rebooted at the same time during planned maintenance.
- This further enhances the availability of your application because it reduces the risk of all VMs being offline simultaneously.

#### Fault Domain

- distributes the VM’s across multiple fault domains.
- A fault domain is a group of physical hardware within an azure datacenter

---

- ! fault domains are focused on handling unexpected failures, while update domains are used for planed maintenances and updates.

---

🟢
![[Pasted image 20231011141858.png | 700]]

----