---
title: identity, access, security
date: 2023-12-06
resources: 
tags:
  - roles
---
# Index

- [[#All roles|All roles]]
- [[#[Differences between Azure roles and Microsoft Entra roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/rbac-and-directory-admin-roles#azure-roles:~:text=Entra%20ID.-,Differences%20between%20Azure%20roles%20and%20Microsoft%20Entra%20roles,-At%20a%20high)|[Differences between Azure roles and Microsoft Entra roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/rbac-and-directory-admin-roles#azure-roles:~:text=Entra%20ID.-,Differences%20between%20Azure%20roles%20and%20Microsoft%20Entra%20roles,-At%20a%20high)]]
# All roles

[[3- All roles]]

---
# [Differences between Azure roles and Microsoft Entra roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/rbac-and-directory-admin-roles#azure-roles:~:text=Entra%20ID.-,Differences%20between%20Azure%20roles%20and%20Microsoft%20Entra%20roles,-At%20a%20high)

| Azure roles                                                                                                               | Microsoft Entra roles                                                                                                                                                                                                                         |
| ------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Manage access to Azure resources                                                                                          | Manage access to Microsoft Entra resources                                                                                                                                                                                                    |
| Supports custom roles                                                                                                     | Supports custom roles                                                                                                                                                                                                                         |
| Scope can be specified at multiple levels (management group, subscription, resource group, resource)                      | [Scope](https://learn.microsoft.com/en-us/azure/active-directory/roles/custom-overview#scope) can be specified at the tenant level (organization-wide), administrative unit, or on an individual object (for example, a specific application) |
| Role information can be accessed in Azure portal, Azure CLI, Azure PowerShell, Azure Resource Manager templates, REST API | Role information can be accessed in the Azure admin portal, Microsoft 365 admin center, Microsoft Graph, AzureAD PowerShell                                                                                                                   |

- If you're a member of the Global Administrator role, However, by default, the <u>Global Administrator doesn't have access to Azure resources</u>.

![[Pasted image 20231206162404.png | 200]]

- #Account_Administrator, #Service_Administrator, and #Co-administrator are the three classic subscription administrator roles in azure.
- <u>can manage resources using the Azure portal.</u>

|Classic subscription administrator|Limit|Permissions|Notes|
|---|---|---|---|
|Account Administrator|1 per Azure account|- Can access the [Azure portal](https://portal.azure.com/#blade/Microsoft_Azure_Billing/SubscriptionsBlade) and manage billing<br>- Manage billing for all subscriptions in the account<br>- Create new subscriptions<br>- Cancel subscriptions<br>- Change the billing for a subscription<br>- Change the Service Administrator<br>- Can't cancel subscriptions unless they have the Service Administrator or subscription Owner role|Conceptually, the billing owner of the subscription.|
|Service Administrator|1 per Azure subscription|- Manage services in the [Azure portal](https://portal.azure.com/)<br>- Cancel the subscription<br>- Assign users to the Co-Administrator role|By default, for a new subscription, the Account Administrator is also the Service Administrator.  <br>The Service Administrator has the equivalent access of a user who is assigned the Owner role at the subscription scope.  <br>The Service Administrator has full access to the Azure portal.|
|Co-Administrator|200 per subscription|- Same access privileges as the Service Administrator, but can’t change the association of subscriptions to Microsoft Entra directories<br>- Assign users to the Co-Administrator role, but can't change the Service Administrator|The Co-Administrator has the equivalent access of a user who is assigned the Owner role at the subscription scope.|


---
