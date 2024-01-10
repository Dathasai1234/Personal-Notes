---
title: doubts
date: 2023-11-24
resources: 
tags:
  - questions/storages
---
1. customer initiate failovers or automated failovers
2. GRS vs RA-GRS, why read access even though we have GRS
3. **storage resource provider** API.
	1. [normal failover in RA-GRS](https://learn.microsoft.com/en-us/azure/storage/common/storage-disaster-recovery-guidance#microsoft-managed-failover:~:text=A%20customer%2Dmanaged%20failover%20loses%20its%20geo%2Dredundancy%20after%20a%20failover%20(and%20failback).%20Your%20storage%20account%20is%20automatically%20converted%20to%20locally%20redundant%20storage%20(LRS)%20in%20the%20new%20primary%20region%20during%20a%20failover%2C%20and%20the%20storage%20account%20in%20the%20original%20primary%20region%20is%20deleted.)
	2. read and write access during **storage** failover [storage resource provider](https://learn.microsoft.com/en-us/azure/storage/common/storage-disaster-recovery-guidance#microsoft-managed-failover:~:text=After%20a%20failover%20is,the%20failover%20is%20complete.).