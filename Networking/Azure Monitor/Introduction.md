---
title: Azure Moniter
date: 2024-01-19
resources: 
tags:
---

> [!note] 
> ![[Archive/Azure_Public_Service_Icons/Icons/monitor/00001-icon-service-Monitor.svg | 50]]
> 
> Monitor is a comprehensive solution of monitoring, analyzing, and responding to the monitoring data collected from your cloud and on-premises.

- It helps you understand
	- how your applications are performing
	- allows you to manually and programmatically respond to system events.

![The diagram above shows an abstracted view of the monitoring process.](https://learn.microsoft.com/en-us/azure/azure-monitor/media/overview/azure-monitor-high-level-abstraction-opt.svg#lightbox)

---

- aggregates the data from every layer and component of your system across multiple Azure and non-Azure subs and tenants.
- It stores it in a common data platform for consumption by a common set of tools that can correlate, analyze, visualize, and/or respond to the data.
- You can also integrate other Microsoft and non-Microsoft tools.

# High Level Architecture of Monitor

![[Pasted image 20240122125040.png]]

- The **[data sources](https://learn.microsoft.com/en-us/azure/azure-monitor/data-sources)** are the types of data collected from each monitored resource.
- The data is collected and routed to the data platforms.
- The data platforms collect stores the collected monitored data.
- Azure Monitor's core data platform has stores for 
	- metrics,
	- logs,
	- traces,
	- changes
- The consumption section shows the components that use the data from the data platform.
- tools to provide
	- Insights
	- Visualize
	- Analyze
	- Respond

---

- Azure Monitor is available the moment you create an Azure subscription.
- The Activity log immediately starts collecting events about activity in the subscription, and platform metrics are collected for any Azure resources you created.

---
# Metrics

[Azure Monitor Metrics](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/data-platform-metrics) stores numeric data from monitored resources into a time-series database.  The metric database is automatically created for each Azure subscription. Use Metrics Explorer to analyze data from Azure Monitor Metrics.
## Types of Metrics

- #Native_Metrics ^e590fb
	- *platform metrics* - metrics that are collected from Azure resources, have no cost and no configurations.
	- *Custom metrics* - metrics collected from different sources that you configure including applications, and agents running on virtual machines.
- #Prometheus_metrics - collected from Kubernetes clusters including Azure Kubernetes service (Ask) and use industry standard tools for analyzing and alerting such as #PromQL and #Grafana.

![[Pasted image 20240122143403.png]]

|**Category** |**Native platform metrics** |**Native custom metrics** |**Prometheus metrics** |
|---|---|---|---|
|Sources|Azure resources|Azure Monitor agent  <br>Application insights  <br>REST API|Azure Kubernetes service (Ask) cluster  <br>Any Kubernetes cluster through remote-write|
|Configuration|None|Varies by source|Enable Azure Monitor managed service for Prometheus|
|Stored|Subscription|Subscription|[Azure Monitor workspace](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/azure-monitor-workspace-overview)|
|Cost|No|Yes|Yes (free during preview)|
|Aggregation|pre-aggregated|pre-aggregated|raw data|
|Analyze|[Metrics Explorer](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-charts)|[Metrics Explorer](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/metrics-charts)|PromQL  <br>Grafana dashboards|
|Alert|[metrics alert rule](https://learn.microsoft.com/en-us/azure/azure-monitor/alerts/tutorial-metric-alert)|[metrics alert rule](https://learn.microsoft.com/en-us/azure/azure-monitor/alerts/tutorial-metric-alert)|[Prometheus alert rule](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/prometheus-rule-groups)|
|Visualize|[Workbooks](https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/workbooks-overview)  <br>[Azure dashboards](https://learn.microsoft.com/en-us/azure/azure-monitor/app/overview-dashboard#create-custom-kpi-dashboards-using-application-insights)  <br>[Grafana](https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/grafana-plugin)|[Workbooks](https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/workbooks-overview)  <br>[Azure dashboards](https://learn.microsoft.com/en-us/azure/azure-monitor/app/overview-dashboard#create-custom-kpi-dashboards-using-application-insights)  <br>[Grafana](https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/grafana-plugin)|[Grafana](https://learn.microsoft.com/en-us/azure/managed-grafana/overview)|
|Retrieve|[Azure CLI](https://learn.microsoft.com/en-us/cli/azure/monitor/metrics)  <br>[Azure PowerShell cmdlets](https://learn.microsoft.com/en-us/powershell/module/az.monitor)  <br>[REST API](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/rest-api-walkthrough) or client library  <br>[.NET](https://learn.microsoft.com/en-us/dotnet/api/overview/azure/Monitor.Query-readme)  <br>[Go](https://pkg.go.dev/github.com/Azure/azure-sdk-for-go/sdk/monitor/azquery)  <br>[Java](https://learn.microsoft.com/en-us/java/api/overview/azure/monitor-query-readme)  <br>[JavaScript](https://learn.microsoft.com/en-us/javascript/api/overview/azure/monitor-query-readme)  <br>[Python](https://learn.microsoft.com/en-us/python/api/overview/azure/monitor-query-readme)|[Azure CLI](https://learn.microsoft.com/en-us/cli/azure/monitor/metrics)  <br>[Azure PowerShell cmdlets](https://learn.microsoft.com/en-us/powershell/module/az.monitor)  <br>[REST API](https://learn.microsoft.com/en-us/azure/azure-monitor/essentials/rest-api-walkthrough) or client library  <br>[.NET](https://learn.microsoft.com/en-us/dotnet/api/overview/azure/Monitor.Query-readme)  <br>[Go](https://pkg.go.dev/github.com/Azure/azure-sdk-for-go/sdk/monitor/azquery)  <br>[Java](https://learn.microsoft.com/en-us/java/api/overview/azure/monitor-query-readme)  <br>[JavaScript](https://learn.microsoft.com/en-us/javascript/api/overview/azure/monitor-query-readme)  <br>[Python](https://learn.microsoft.com/en-us/python/api/overview/azure/monitor-query-readme)|[Grafana](https://learn.microsoft.com/en-us/azure/managed-grafana/overview)|

- #Activity_log
	- sub level events that track operations for each Azure resource.  for example, creating a new resource or starting a virtual machine.z
	- Activity log events are automatically generated and collected for viewing in the Azure portal.
	- You can create a <u>diagnostic setting</u> to send the activity log to Azure Monitor Logs.
- #platform_matrics
	- Numerical values that are automatically collected at regular intervals and describe some aspect of a resource at a particular time. 
	- Platform metrics are automatically generated and collected in Azure Monitor Metrics.
- #resource_logs 
	- Provide insight into operations that were performed by an Azure resource.
	- Operation examples might be getting a secret from a key vault or making a request to a database.
	- Resource logs are generated automatically, but you must create a diagnostic setting to send them to Azure Monitor Logs.
- #Virtual_machine_guest_metrics_and_logs
	- Performance and log data from the guest operating system of Azure virtual machines.
	- You must install an agent on the virtual machine to collect this data and send it to Azure Monitor Metrics and Azure Monitor Logs.