---
title: 
date: 2024-09-28
resources: 
tags:
---
# Volume per day basis

```kql
Usage
| where TimeGenerated > ago(30d)
| where IsBillable == true
| summarize TotalVolumeGB = sum(Quantity) / 1024 by bin(TimeGenerated, 1d)
```

# Overall Volume in workspace

```kql
Usage
| where TimeGenerated > ago(30d)
| where IsBillable == true
| summarize TotalVolumeGB = sum(Quantity) / 1024
```

