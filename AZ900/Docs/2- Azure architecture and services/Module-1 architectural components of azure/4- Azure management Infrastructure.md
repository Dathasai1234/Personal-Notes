
- [[#Azure resources and resource groups|Azure resources and resource groups]]
- [[#Azure Subscriptions|Azure Subscriptions]]
	- [[#Azure Subscriptions#Billing Boundary|Billing Boundary]]
	- [[#Azure Subscriptions#Access control boundary|Access control boundary]]
- [[#Azure management groups|Azure management groups]]
- [[#Management group, subscriptions, and resource group hierarchy|Management group, subscriptions, and resource group hierarchy]]


Includes

1. resources,
2. resource groups,
3. subscriptions,
4. accounts

## Azure resources and resource groups

- & Anything you Create, provision, deploy etc is a resource.

- VM’s
- virtual Networks
- databases,
- cognitive services

Considered resources in Azure.

![[Pasted image 20231005143806.png | 500]]

- Resource groups are simply <u>groupings of resources</u>.
- When you create a *resource*, you’re required to place it into a *resource group*.
- While a resource group can contain many resources, 
- <u>a single resource can only be in one resource group</u> at a time.
- Some resources may be moved between resource groups, but when you move a resource to a new group, it will no longer be associated with the former group.
- Additionally, <u>resource groups can't be nested</u>, meaning you can’t put resource group B inside of resource group A.

- Resource groups provide a convenient way to group resources together.
- When you apply an <u>action</u> to a resource group, that action will apply to all the resources within the resource group.
- If you delete a resource group, all the resources will be deleted.
- If you grant or deny access to a resource group, you’ve granted or denied access to all the resources within the resource group.

---
## Azure Subscriptions

- & unit of management, billing, and scale.

- Similar to how resource groups are a way to logically organize resources, subscriptions allow you to logically organize your resource groups and facilitate billing.

![[Pasted image 20231005151344.png | 500]]

- You can use Azure subscriptions to define boundaries around Azure products, services, and resources.
- There are two types of subscription boundaries that you can use:
	- Billing boundary
	- Access control boundary

### Billing Boundary

- Determines how an Azure account is billed for using Azure.
- You can create multiple subscriptions for different types of billing requirements.
- Azure generates separate billing reports and invoices for each subscription so that you can organize and manage costs.

### Access control boundary

- Azure applies access-management policies at the subscription level,
- you can create separate subscriptions to reflect different organizational structures.
- An example is that within a business, you have different departments to which you apply distinct Azure subscription policies. This billing model allows you to manage and control access to the resources that users provision with specific subscriptions.

## Azure management groups

1. Resources are gathered into resource groups.
2. resource groups are gathered into subscriptions.

imagine if you’re dealing with <u>multiple applications, multiple development teams, in multiple geographies</u>.

1. You organize subscriptions into containers called **management groups**
2. Apply **governance conditions** to the management groups.
3. All subscriptions within a management group automatically inherit the conditions applied to the management group.
4. resource groups *inherit* settings from subscriptions
5. resources inherit from resource groups.
6. Management groups give you enterprise-grade management at a large scale, no matter what type of subscriptions you might have. Management groups can be nested.

## Management group, subscriptions, and resource group hierarchy

management groups
	⬇
subscriptions
	⬇
resource groups
	⬇
resources
![[Pasted image 20231005172047.png | 500]]

---