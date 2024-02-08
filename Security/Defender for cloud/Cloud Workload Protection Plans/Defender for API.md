---
title: Cloud Workload Protection Plans
date: 2024-02-08
resources: 
tags:
---

- API (Application Programming Interface)
- Core of communication for applications to interact each other.
- Most of web traffic is driven by API's
- API's are expected some information that could be potentially valuable for external threat actors.
- The web applications are the attack surface which is the most vulnerable area for the exploitations.
- The blind thinking of having a WAF for securing web applications is not enough for API security.
- WAF's can provide a layer of protectivity for your applications but does not have any default protection and does not look deep into protection for API's.
- There are new set of API risks and vulnerabilities which are coined by OWASP API top 10.
- #BOLA stands for *Broken Object Level Authorization*.
	- It occurs when an application or API grants access to data objects based on *user roles*,
	- but *fails to verify* if the user is authorized to access **specific** objects within those roles.
	- This vulnerability allows attackers to bypass authorization and access sensitive data or perform unauthorized actions.

%%
# BOLA Example

Imagine you're running an online store with an API for users to manage their accounts and orders. Here's how BOLA could play out:

**Scenario:**

- Users have roles like "Customer" and "Admin" with different permissions.
- "Customers" can view their own orders and personal information.
- "Admins" can view and manage all orders and user accounts.

**BOLA Vulnerability:**

- The API lacks fine-grained authorization for **individual orders**. It only checks the user's role, not if they have specific access to an order.
- An attacker intercepts a "Customer" session ID and injects it into a request to view another customer's order details.

**Exploitation:**

- Since the API only checks the "Customer" role, it grants access to the attacker's request, revealing another customer's order information (violation of privacy).
- This could be escalated further if the attacker manipulates order IDs to access sensitive admin data or even modify orders.
%%

- By enabling the *defender for API* plan, it unifies all the APIs into single pane.
- It can get us all the API's that they're managing in their Azure API Management Services in one single plate, and then we bring in insights which can help customer to understand APIs to be correctly configured with respect to authentication checks.
- The power of both rule based detection of known threats and understanding un-known threats through our ML based detections.