---
title: Governance
date: 2023-12-19
resources: 
tags:
---
# Effects

1. Append
2. Audit
3. AuditIfNotExists
4. Enforcement effects [source](https://learn.microsoft.com/en-us/azure/governance/policy/overview#:~:text=Start%20with%20an,already%20in%20place.)
	1. Deny
	2. modify
	3. DeployIfNotExists
5. Disabled

---
# Policy vs RBAC

- #policy evaluates state by examining properties on resources that are represented in resource manager and properties of some resource providers.
- Ensures that resource state is compliant to your business rules without concern for who made the change or who has permission to make a change.

- #RBAC managing user actions on diff scopes.
- Even if an individual has access to perform an action, if the result is a non-compliant resource, Azure Policy still blocks the create or update.

- The combination of Azure RBAC and Azure Policy provides full scope control in Azure.

---
# RBAC permissions in azure policy

- #resource_policy_contributor - includes most policy operations.
- Both Reader and Contributor have access to all read Azure policy operations.

- **Contributor** may trigger resource remediation, but can't _create_ or _update_ definitions and assignments.
- All Policy objects, including definitions, initiatives, and assignments, will be readable to all roles over its scope. For example, a Policy assignment scoped to an Azure subscription will be readable by all role holders at the subscription scope and below.

---
# Initiative definitions and assignments

- We recommend creating and assigning initiative definitions even for a single policy definition. For example, you have policy definition _policyDefA_ and create it under initiative definition _initiativeDefC_. If you create another policy definition later for _policyDefB_ with goals similar to _policyDefA_, you can add it under _initiativeDefC_ and track them together.
    
    - Once you've created an initiative assignment, policy definitions added to the initiative also become part of that initiative's assignments.
        
    - When an initiative assignment is evaluated, all policies within the initiative are also evaluated. If you need to evaluate a policy individually, it's better to not include it in an initiative.

---
# Policy parameters

- #policy_parameters help simplify your policy management by reducing the number of policy definitions you must create. [source](https://learn.microsoft.com/en-us/azure/governance/policy/overview#:~:text=Definition%20Structure.-,Policy%20parameters,-help%20simplify%20your)