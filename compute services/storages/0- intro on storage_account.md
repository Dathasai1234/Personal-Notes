---
title: storages
date: 2023-11-22
resources: 
tags:
  - storages
---

# Table of Contents

- [[#Creating a storage account|Creating a storage account]]
- [[#Access Level|Access Level]]
- [[#Pricing|Pricing]]
- [[#Access tires|Access tires]]
	- [[#Access tires#Access tires for **premium block blobs storage**|Access tires for **premium block blobs storage**]]
- [[#Life cycle management rules|Life cycle management rules]]
	- [[#Life cycle management rules#for general storage account|for general storage account]]
	- [[#Life cycle management rules#for premium Storage account|for premium Storage account]]
- [[#Redundancy|Redundancy]]
- [[#Difference between **Availability** and **Durability**|Difference between **Availability** and **Durability**]]
- [[#Premium performance|Premium performance]]
	- [[#Premium performance#premium account type|premium account type]]
- [[#Azure Files|Azure Files]]
	- [[#Azure Files#Azure files deployment|Azure files deployment]]
- [[#Blob rehydration from Archive tire|Blob rehydration from Archive tire]]


---

- storage accounts
	- containers
	- File shares
	- Queues
	- Tables

> Storage accounts are the management service that serves five different azure storage services.
# Creating a Storage account

- Basic tab
	- Instance details
		- storage account name
		- Region
		- performance
			- Standard
			- Premium
		- Redundancy
			- LRS
			- GRS
			- ZRS
			- GZRS

---
# Access Level

- can change the **access level** to a particular container.
	- private (no anonymous access)
	- Blob (anonymous access)
	- Container (anonymous read access for containers and blobs)

---
# Pricing

Depends on multiple factors
- Volume of data stored per month.
- Quantity and types of operations performed, along with any data transfer costs.
- Data redundancy option selected.

---
# Access Tires

- Hot
	- accessed more frequently
	- high storage costs
	- lower access costs
	- can set hot access tier at the storage level
- cool
	- accesses or modified infrequently
	- lower storage costs
	- higher access costs compared to hot tier
	- data needs to be stored for at-least **30 days**
	- can set cool access tier at the storage level
- archive
	- rarely accessed
	- lower storage costs
	- higher access costs compared to cool access tier
	- data needs to be stored at-least **180 days**
	- can set archive access tier at the blob level

- default tier of a blob in a container is blob.
- ! This default hot tier can be changed to cool tier in the storage account configuration.
- existing files with default hot tier will change to cool tier.
- ! Changing the default **hot or cold** tire will change the existing **hot (inferred)** or **cold (inferred)** , but it will not change the **hot** and **cold** blobs tire which are selected specifically during the upload.
- new blobs will default come under cool tier.

<br>

- **early deletion penalty** if it's deleted or moved to a different tier before 30 days has elapsed.
- For a blob in the cold tier, the deletion penalty applies if it's deleted or moved to a different tier before 90 days has elapsed. 
- For example, if a blob is moved to the cool tier and then deleted after 21 days, you'll be charged an early deletion fee equivalent to 9 (30 minus 21) days of storing that blob in the cool tier.

<br>

- changing tier at blob level will give an additional tier called archive tier.
- ! Setting the access tier to “Archive” will make your blob inaccessible until it is rehydrated back to “Hot” or “Cool”, which may take several hours.

## Access Tires for **premium Block Blobs storage**

> [!important]
> Data stored in a premium block blob storage account cannot be tiered to hot, cool, cold or archive.
> - [source](https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-overview#:~:text=Data%20stored%20in%20a%20premium%20block%20blob%20storage%20account%20cannot%20be%20tiered%20to%20hot%2C%20cool%2C%20cold%20or%20archive%20by%20using%20Set%20Blob%20Tier%20or%20using%20Azure%20Blob%20Storage%20lifecycle%20management.)

---
# Life Cycle Management Rules

## For General Storage account

![[Pasted image 20231127192103.png | 500]]

> [!Note]
> - The general storage account allows to change tire of the blobs between hot, cool and archive.
> - So the lifecycle management shows all the changing options depending on the conditions

## For Premium Storage account

![[Pasted image 20231127192019.png | 500]]

> [!note]
> - The premium storage account does not directly allow to change tires for the block blobs.
> - - So the lifecycle management does not show all the tire change options except the delete option.

- You can't rehydrate an archived blob to an online tier by using lifecycle management policies.

---
# Redundancy

![[Data redundancy]]

# Difference between **Availability** and **Durability**

- Durability refers to how safe data is from being lost.
- While data availability refers to how often you can access your stored data.

---

# Premium Performance

## Premium account Type

1. Block blobs
2. File share
3. page blobs

- only **LRS** and **ZRS**

---
# Azure Files

- [defination](https://learn.microsoft.com/en-us/azure/storage/files/storage-files-introduction#:~:text=Azure%20Files%20offers%20fully%20managed%20file%20shares%20in%20the%20cloud%20that%20are%20accessible%20via%20the%20industry%20standard%20Server%20Message%20Block%20(SMB)%20protocol%2C%20Network%20File%20System%20(NFS)%20protocol%2C%20and%20Azure%20Files%20REST%20API.)
- You can access the files from anywhere in the world using a URL that points to the file
- And includes a shared access signature (SAS) token. 
- You can generate SAS tokens. they allow specific access to a private asset for a specific amount of time.
- Configuration files can be stored on a file share and accessed from multiple VMs.
- Tools and utilities used by multiple developers in a group can be stored on a file share, ensuring that everybody can find them, and that they use the same version.
- SMB Azure file shares are accessible from Windows, Linux, and macOS clients.
- NFS Azure file shares are accessible from Linux clients

## Azure Files Deployment

2 ways

1. Directly mounting the serverless azure **file shares**
2. Caching Azure file shares on-premises using Azure **File sync**

---
# Blob Rehydration from Archive Tire

[source](https://learn.microsoft.com/en-us/azure/storage/blobs/archive-rehydrate-overview#:~:text=While%20a%20blob,online%20tier.)

2 options to access the archived blob

1. copy the archived blob to a new blob in the hot or clod tire
2. rehydrating the archived blob to the online tire using *set Blob Tire* operation

- rehydration of an archive blob may take several hours to complete
- archiving the larger blobs for best optimal performance when rehydrating
- rehydrating large number of small blob may require extra time due to processing overhead on each blob.
- while rehydration, source and destination names should be different
- copying of archived blobs will only happen when *the destination and source account must be in the same region.*
![[Pasted image 20231124154924.png | 300]]

- After the copy operation is complete, the destination blob appears in the archive tier.
- The destination blob is then rehydrated to the online tier that you specified in the copy operation.
- When the destination blob is fully rehydrated, it becomes available in the new online tier.

---