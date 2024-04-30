---
title: Cloud Workload Protection Plans
date: 2024-02-08
resources: 
tags:
---

# Index

- [[#Defender for Key-vault|Defender for Key-vault]]

# Defender for Key-vault

The azure key vault is used to store *keys*, *Certificates* and *Secrets*

**Keys** - a file with plain string used to decrypt an encrypted information.

**Certificates** - They are used as an identity. Commonly used to represent an identity of an application to another application for may be a secure communication.

- Microsoft Defender for Key Vault detects unusual and potentially harmful attempts to access or exploit Key Vault accounts.
- ! Microsoft Defender for Key Vault is designed to help identify suspicious activity caused by stolen credentials. **Don't** dismiss the alert simply because you recognize the user or application. Contact the owner of the application or the user and verify the activity was legitimate. You can create a suppression rule to eliminate noise if necessary. Learn more in [Suppress security alerts](https://learn.microsoft.com/en-us/azure/defender-for-cloud/alerts-suppression-rules).

- [x] [Suppressing false positives or other unwanted security alerts - Microsoft Defender for Cloud | Microsoft Learn](https://learn.microsoft.com/en-us/azure/defender-for-cloud/alerts-suppression-rules) ⏫ ✅ 2024-04-29

---