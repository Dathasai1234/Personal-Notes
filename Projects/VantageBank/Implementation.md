---
title: VantageBank
date: 2024-07-18
resources: 
tags:
---

# Recommended Analytics Rules

SNP recommended enabling the below-mentioned rules based on the data connectors connected in the Vantage environment.

**AzureActiveDirectory**

1. Brute force attack against a Cloud PC- Identifies evidence of brute force activity against a Windows 365 Cloud PC by highlighting multiple authentication failures and by a successful authentication within a given time window.

2. Failed login attempts to Azure Portal - Identifies failed login attempts in the Microsoft Entra ID Signin Logs to the Azure Portal. Many failed logon attempts or some failed logon attempts from multiple IPs could indicate a potential brute force attack.

3. Multiple admin membership removals from newly created admin -  This query detects when newly created Global admin removes multiple existing global admins which can be an attempt by adversaries to lock down organization and retain sole access. Investigate reasoning and intention of multiple membership removal by new Global admins and take necessary actions accordingly.

**Azure activity**

4. Suspicious number of resource creation or deployment activities - Indicates when an anomalous number of VM creations or deployment activities occur in Azure via the AzureActivity log.

Action steps –

* Verify the activity with the IT team on any planned activity is there in the environment.
* Verify with the user who created the resources if is there business requirements for deploying the resources
* Verify the audit logs and Azure activity logs for the root case

5. Rare subscription-level operations in Azure - This query looks for a few sensitive subscription-level events based on Azure Activity Logs

Action Steps –

- Verify the activity with the user and check the requirements of change in the subscription level
- If it is not a legitimate operation, verify all the activity logs of the user
- Verify all audit logs and sign logs for root case analysis

6. Suspicious granting of permissions to an account - Identifies IPs from which users grant access to other users on Azure resources and alerts when a previously unseen source IP address is used.

**Microsoft Defender for Cloud Apps**
  
7. Linked Malicious Storage Artifacts - This query identifies the additional files uploaded by the same IP address which triggered a malware alert for malicious content upload on Azure Blob or File Storage Container.

**Microsoft 365**

8. Multiple users email forwarded to same destination - Identifies when multiple users mailboxes are configured to forward to the same destination. This could be an attacker-controlled destination mailbox configured to collect mail from multiple compromised user accounts.

9. Accessed files shared by temporary external user - This detection identifies an external user is added to a Team or Teams chat and shares a files which is accessed by many users (>10) and the users is removed within short period of time. This might bean indicator of suspicious activity.

10. External user added and removed in short timeframe - This detection flags the occurrences of external user accounts that are added to a Team and then removed within one hour.