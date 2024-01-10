---
title: Presentations
date: 2023-12-05
resources: 
tags:
  - questions/presentation-1
---
1. Difference about Availability Zone and Scale Sets
2. $ While deploying the vm check the storage available (resize) ^72c779
3. $ What happens if we don't delete the files in the access tier of Blob after the number of days? ^983e33
4. $ Can we update the azure disk storage types such that Standard hdd can be updated to standard ssd?  Temporary vs Managed disk ^dc4692
5. $ Priority order of the disks Disk>Blobs>Files>tables>Queues
6. ! Transaction optimized tier in azure blob storage
7. $ Can we update from grs to zrs or vice versa Or other redundancy ^49742b
8. GRS VS RAGRS cost vs access and need and possibilities of switching between them. (adding extra permutations of the possibilities will be better).
9. $ Why is AzCopy only unidirectional and how do you connect Azure to your CMD. What are the prerequisites? ^e5e9af
10. $ Lifecycle Management in Azure Storage ^3aa22e


---

![[Questions#^72c779]]

- After deploying the VM, we are able to change the size of the ram memory
- You can expand data disks without deallocating your VM. [source](https://learn.microsoft.com/en-us/azure/virtual-machines/windows/expand-os-disk#:~:text=You%20can%20expand%20data%20disks%20without%20deallocating%20your%20VM.)
	- if data disk size is less than 4TB, should deallocate or detach to the VM to expand
	- more than 4TB, you can expand the disk size without deallocation or detach to VM.
- The new size should be greater than the existing disk size.
- The maximum allowed is 4,095 GB for OS disks.
- after extending the size, extend the VM Disk size in *diskpart* of the VM.
<br>
- The temporary storage is erased as you restart or stop and start the VM
- The newly attached dataDisk can be used if you want to persist the data in the VM.

---


![[Questions#^983e33]]

The files remain there till we add a policy or rule to change to different tire. The rules can be added in life-cycle management.

---

![[Questions#^dc4692]]

- I don’t think we have that much control to change from SSD to HDD of the default disk of a VM.
- We can attach another disk of SSD or HDD to that VM.

---

![[Questions#^49742b]]

![[Pasted image 20231205105328.png | 700]]

- We can convert from GRS to RA-GRS.
- failover is only available for GRS and RA-GRS
- There will be no data loss or application down-time
- Redundancy cannot be changed during while failover is in process.

![[Pasted image 20231205105549.png | 700]]

---

![[Questions#^e5e9af]]

- Azcopy cannot be bi-directional at a time. interchanging source and destination will change the direction.
- Azcopy can be connected to CMD by downloading and interact with that utility using terminal.

---

![[Questions#^3aa22e]]


In the lifecycle management, you can add rules to change the blob tires automatically at certain condition in the storage accounts.

---