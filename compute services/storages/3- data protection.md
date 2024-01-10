---
title: storages
date: 2023-11-28
resources: https://learn.microsoft.com/en-us/azure/storage/blobs/versioning-overview
tags:
  - storages
  - soft-delete
---
# Table of contents

- [[#Soft-delete|Soft-delete]]
	- [[#Soft-delete#blob soft delete|blob soft delete]]
- [[#blob-versioning|blob-versioning]]
	- [[#blob-versioning#Version ID|Version ID]]
	- [[#blob-versioning#blob-version and blob-snapshot|blob-version and blob-snapshot]]
- [[#Pricing and billing|Pricing and billing]]

# Soft-delete

- protects data from being accidentally deleted .
- maintains the deleted data in the system for a specific period of time.
- During **retention period**, you can restore a soft-deleted container and its contents to the containers state at the time it was deleted.
- container and its contents are permanently deleted after the period expire.

<br>

- ! default retention period is *7 days*
- you can specify a retention period between 1 and 365 days.
- you can recover a deleted container by calling the *Restore Container Operation*.
- containers blobs and any blob versions and snapshots are also restored.
- ? use container soft delete to restore blobs when container itself was deleted.
- To restore a deleted blob when its parent container hasn’t been deleted, you must use *soft delete* or *blob versioning* 
- you must restore it to its original name. If the original name has been used to create a new container, then you will not able to restore the soft-delete container.
- [source](https://learn.microsoft.com/en-us/azure/storage/blobs/soft-delete-container-overview#:~:text=Container%20soft%20delete%20can,the%20soft%2Ddeleted%20container.)
- You can change the retention period at any time.
- ! updated retention period applies only to the newly deleted containers.
- Previous deleted containers will be permanently deleted based on the retention period that was in effect at the time that the container was deleted.
- [source](https://learn.microsoft.com/en-us/azure/storage/blobs/soft-delete-container-overview#:~:text=You%20can%20change%20the%20retention%20period%20at%20any%20time%2C%20but%20keep%20in%20mind%20that%20an%20updated%20retention%20period%20applies%20only%20to%20newly%20deleted%20containers.%20Previously%20deleted%20containers%20will%20be%20permanently%20deleted%20based%20on%20the%20retention%20period%20that%20was%20in%20effect%20at%20the%20time%20that%20the%20container%20was%20deleted.)
- Disabling container soft delete doesn’t result in permanent deletion of containers that were previously soft-deleted.
- ! use resource locks for accidental deletion of storage account. Soft-delete does not protect against the deletion of storage account.

<br>

- container soft delete is available in
	- General-purpose V2 and V1 storage accounts.
	- Block blob storage accounts.
	- Blob storage accounts.

## blob soft delete

- protects an individual *blob*, *snapshots*, or *version* from accidental deletes or overwrites for specific period of time. 

---
# blob-versioning

- ! every write operation will create a new version of that blob after you enable blob versioning for a storage account.
- For this reason, it may result in additional costs.
- Use lifecycle management to automatically delete old versions of the blob.
- captures the state of a blob at a given point of time.
- each version is identified with unique ID.
- A blob can have only one current version at a time.
## how version works when **blob creation** and **deletion**

- When you create a new blob, a single version exists. 
- that version is the current version.
- When you modify an existing blob, the current version becomes the previous version.
- A new version is created to capture the updated state, and that new version is the current version.
- When you delete a blob, the current version of the blob becomes a previous version.
- and there’s no longer a current version.
- Any previous versions of the blob persists.
- [source](https://learn.microsoft.com/en-us/azure/storage/blobs/versioning-overview#:~:text=When%20you%20create,the%20blob%20persist.)
- previous version can be promoted to a current version.
- ![[Pasted image 20231128131640.png | 500]]
- ![[Pasted image 20231129113358.png | 700]]
- ![[Pasted image 20231128132731.png | 500]]
<br>
- having large number of versions per blob increase the latency for blob listing operations.
- Microsoft recommends maintaining fewer than 1000 versions per blob.
- use lifecycle management to auto delete the versions.
- ? versioning supported
	- general-purpose V2
	- premium block blob
	- legacy blob storage accounts
- ? not supported
	- data lake Storage Gen 2.
- Disabling blob versioning doesn’t delete existing blobs. No new versions are subsequently created.
- restoring a soft delete d version using [**Un-delete Blob** operation](https://learn.microsoft.com/en-us/azure/storage/blobs/versioning-overview#:~:text=Restoring%20soft%2Ddeleted%20versions%20with%20the%20Undelete%20Blob%20operation%20doesn%27t%20promote%20any%20version%20to%20be%20the%20current%20version.%20To%20restore%20the%20current%20version%2C%20first%20restore%20all%20soft%2Ddeleted%20versions%2C%20and%20then%20use%20the%20Copy%20Blob%20operation%20to%20copy%20a%20previous%20version%20to%20a%20new%20current%20version.)
- ![[Pasted image 20231128133656.png | 600]]

---
- deleted a blob.
- created a blob with the **same name** of the deleted blob.
- try to undelete the deleted blob.
- ![[Pasted image 20231129114603.png | 400]]

---
## Version ID

[source](https://learn.microsoft.com/en-us/azure/storage/blobs/versioning-overview#:~:text=storage%20account.-,Version%20ID,version%20ID%20remains%20the%20same%20for%20the%20lifetime%20of%20the%20version.,-Versioning%20on%20write)

## blob-version and blob-snapshot

- A snapshot is created manually by you or your application
- A version is created automatically on a write or delete operation.

> [! important]
> It is recommended to update your applications to *stop taking snapshots* of block blobs, if versioning is enabled for your storage account.
> - If versioning is enabled for your storage account, all updates and deletions are captures and preserved by versions.
> - Taking snapshots does not offer any additional protection to your block blob data if blob versioning is enabled, **and may increase costs and application complexity**

- When you take a snapshot of a versioned blob, a new version is created at the same time that the snapshot is created.
- A new current version is also created when a snapshot is taken.
- [source](https://learn.microsoft.com/en-us/azure/storage/blobs/versioning-overview#:~:text=When%20you%20take%20a%20snapshot%20of%20a%20versioned%20blob%2C%20a%20new%20version%20is%20created%20at%20the%20same%20time%20that%20the%20snapshot%20is%20created.%20A%20new%20current%20version%20is%20also%20created%20when%20a%20snapshot%20is%20taken.) 
- ![[Pasted image 20231128130127.png | 400]]
- blob version and snapshots with version ID 2 and 3 contain identical data.

---
# point-in-time restore

![[Pasted image 20231129115153.png | 800]]

---
# Pricing and billing

- no additional costs to enable container soft delete.
- Data in soft-delete containers is billed at the same rate as active data.

---