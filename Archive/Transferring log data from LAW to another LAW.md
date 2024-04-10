---
title: Archive
date: 2024-04-01
resources: 
tags:
---

## Things to Do

1. Creating a custom destination table for the event hub data in log analytic workspace.
2. DCE
3. DCR
4. Grant DCR permissions in EventHub
5. Associate DCR to EventHub.

## Prerequisites

All resources in same region

- LAW
	- Needs to be linked to a dedicated cluster
	- Or have a commitment tire
- EventHub namespace with public network access

## Gather Info

Subscription ID - 
```
f77f3e58-d03d-49e0-9284-05b69f4bedbc
```

Resource group name - 
```
sentinel-rg
```

Workspace name - 
```
Sentinel-LAW
```

Workspace resource ID - 
```
/subscriptions/f77f3e58-d03d-49e0-9284-05b69f4bedbc/resourcegroups/sentinel-rg/providers/microsoft.operationalinsights/workspaces/sentinel-law
```

Event hub instance resource ID - 
```

```

## Dest Table in LAW

You can ingest data into custom table in LAW.

- In cloud shell

```powershell
$tableParams = @'
{
    "properties": {
        "schema": {
            "name": "kdsc-table_CL",
            "columns": [
                {
                    "name": "TimeGenerated",
                    "type": "datetime",
                    "description": "The time at which the data was ingested."
                },
                {
                    "name": "RawData",
                    "type": "string",
                    "description": "Body of the event."
                },
                {
                    "name": "Properties",
                    "type": "dynamic",
                    "description": "Additional message properties."
                }
            ]
        }
    }
}
'@

Invoke-AzRestMethod -Path "/subscriptions/a263304e-8647-497f-89cc-79bdd0ae18ea/resourcegroups/kdsc-testlab-2/providers/microsoft.operationalinsights/workspaces/log-workspace-src/tables/kdsc-table_CL?api-version=2021-12-01-preview" -Method PUT -payload $tableParams
```

## DCE

- To collect data with a data collection rule, you need a data collection endpoint:
- **Resource id** of DCE - */subscriptions/a263304e-8647-497f-89cc-79bdd0ae18ea/resourceGroups/kdsc-testlab-2/providers/Microsoft. Insights/dataCollectionEndpoints/mydatacollectionendpoint*

## DCR

- Azure Monitor uses data collection rules to define which data to collect, how to transform that data, and where to send the data.

`template > deploy a custom template > build your own template in the editor`

Paste the below resource manager template

```json
{
    "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {
        "dataCollectionRuleName": {
            "type": "string",
            "metadata": {
                "description": "Specifies the name of the data collection Rule to create."
            }
        },
        "workspaceResourceId": {
            "type": "string",
            "metadata": {
                "description": "Specifies the Azure resource ID of the Log Analytics workspace to use."
            }
        },
        "endpointResourceId": {
            "type": "string",
            "metadata": {
                "description": "Specifies the Azure resource ID of the data collection endpoint to use."
            }
        },
        "tableName": {
            "type": "string",
            "metadata": {
                "description": "Specifies the name of the table in the workspace."
            }
        },
        "consumerGroup": {
            "type": "string",
            "metadata": {
                "description": "Specifies the consumer group of event hub."
            },
            "defaultValue": "$Default"
        }
    },
    "resources": [
        {
            "type": "Microsoft.Insights/dataCollectionRules",
            "name": "[parameters('dataCollectionRuleName')]",
            "location": "[resourceGroup().location]", 
            "apiVersion": "2022-06-01",
            "identity": {
                             "type": "systemAssigned"
              },
            "properties": {
                "dataCollectionEndpointId": "[parameters('endpointResourceId')]",
                "streamDeclarations": {
                    "Custom-MyEventHubStream": {
                        "columns": [
                {
                    "name": "TimeGenerated",
                    "type": "datetime"
                },
                {
                    "name": "RawData",
                    "type": "string"
                },
                {
                    "name": "Properties",
                    "type": "dynamic"
                }
            ]
                    }
                },
                "dataSources": {
                    "dataImports": {
                         "eventHub": {
                                    "consumerGroup": "[parameters('consumerGroup')]",
                                    "stream": "Custom-MyEventHubStream",
                                    "name": "myEventHubDataSource1"
                                                          }
                                           }
               },
                "destinations": {
                    "logAnalytics": [
                        {
                            "workspaceResourceId": "[parameters('workspaceResourceId')]",
                            "name": "MyDestination"
                        }
                    ]
                },
                "dataFlows": [
                    {
                        "streams": [
                            "Custom-MyEventHubStream"
                        ],
                        "destinations": [
                            "MyDestination"
                        ],
                        "transformKql": "source",
                        "outputStream": "[concat('Custom-', parameters('tableName'))]"
                    }
                ]
            }
        }
    ]
}
```

![[Pasted image 20240404153726.png | 400]]

- Expand the **Deployment details** box, and select your data collection rule to view its details. Select **JSON View**.
- Copy the **Resource ID** for the data collection rule.

![[Pasted image 20240404192910.png]]

## Grant the Event Hub Permission to the Data Collection Rule

From the event hub or Event Hubs namespace in the Azure portal, select **Access Control (IAM)** > **Add role assignment**.

**Azure Event Hubs Data Receiver** > Select **Managed identity** for **Assign access to** and click **Select members**.

![[Pasted image 20240404154200.png]]

Review + assign

## Associate the Data Collection Rule with the Event Hub

