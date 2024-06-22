---
title: Sentinel
date: 2024-06-20
resources: 
tags:
---

- [x] SIEM. ✅ 2024-06-20
- [x] SOAR. ✅ 2024-06-20
- [x] Prerequisites for Sentinel Deployment. ✅ 2024-06-20
- [x] Design Considerations of Sentinel. ✅ 2024-06-20
- [x] Trial period of Sentinel. ✅ 2024-06-20
- [ ] Costs in Log analytic Workspace.
	- [ ] Tiers of LAW.
	- [ ] Retention Period of Sentinel and LAW.
	- [ ] Table plans.
- [ ] Restoration from archival period.
- [ ] Data Collection in Sentinel (Data Collectors).
- [ ] Workbooks.
	- [ ] Workspace Usage Report.
- [ ] Incidents.
- [ ] UEBA.
- [ ] TI in Sentinel.

- _ingest data_, _monitor data_, _hunt_, _investigate_, _respond, and connect_ with different products, platforms, and services.

## Example

Company named agent, wants SIEM solutions and want to adopt Sentinel for as a SIEM solution. Two kinds of Organizations

- Free Trial of Sentinel.
	- When you enable Sentinel on a workspace, 10 GB/day is free for 31 days.
	- This free trial is subject to a 20-workspace limit per Azure tenant.

| Tier              | Microsoft Sentinel Price | Effective Per GB Price1 | Savings Over Pay-As-You-Go |
| ----------------- | ------------------------ | ----------------------- | -------------------------- |
| Pay-As-You-Go     | $4.30 per GB             | $4.30 per GB            | N/A                        |
| 100 GB per day    | $296 per day             | $2.96 per GB            | 31%                        |
| 200 GB per day    | $548 per day             | $2.74 per GB            | 36%                        |
| 300 GB per day    | $800 per day             | $2.67 per GB            | 38%                        |
| 400 GB per day    | $1,037.33 per day        | $2.60 per GB            | 40%                        |
| 500 GB per day    | $1,265 per day           | $2.53 per GB            | 41%                        |
| 1,000 GB per day  | $2,480 per day           | $2.48 per GB            | 42%                        |
| 2,000 GB per day  | $4,800 per day           | $2.40 per GB            | 44%                        |
| 5,000 GB per day  | $11,550 per day          | $2.31 per GB            | 46%                        |
| 10,000 GB per day | $22,240 per day          | $2.23 per GB            | 48%                        |
| 25,000 GB per day | $53,450 per day          | $2.14 per GB            | 50%                        |
| 50,000 GB per day | $1,02,600 per day        | $2.06 per GB            | 52%                        |