---
title: Presentation-1
date: 2023-11-14
resources: 
tags:
  - Compute
---

Web Applications / APIs / Containers
Multiple apps per instance
Typically Stateless or Externalised State
Includes High Availability
**Can scale out to 20 instances per plan
Can apply IP restrictions on the frontend (So always has public IP address)
Multi-tenanted Service
Can be integrated with virtual network / hybrid**
SLA:    99.95%

> If you are looking to have a fully managed hosting platform for hosting web and mobile applications, App service is a place to go.

hassle of managing things,
patching things
choosing number of instances
scaling it
It's literally you drag a slider to auto scale that's it.

---

**Multi-tenancy in Azure App Service means:**

1. **Shared Space:** Imagine you have a big building, and each floor is like a separate space for a different company. These companies are the "tenants." They share the same building (like how multiple users share the same Azure App Service environment).
    
2. **Independence:** Each company on a floor does its own thing without interfering with others. Similarly, in Azure App Service, each tenant (customer or organization) has its own area to run its web applications. They don't mess with each other's stuff.
    
3. **Resource Sharing:** Think of resources like electricity and water in the building. All companies share these resources, making it cost-effective. In Azure App Service, different tenants share computing power and other resources to save money.
    
4. **Scaling:** Each company can adjust its office size based on its needs. Similarly, in Azure App Service, tenants can change the resources they use for their applications based on how much they need at a given time.
    
5. **Security:** Security is like having separate locks for each office. In Azure App Service, each tenant's data and applications are kept secure and separate from others. They have their own "keys" to access their space.
    
6. **Customization:** Each company can have its own sign and decoration. In Azure App Service, tenants can use custom domains and SSL certificates to give their applications a unique and branded identity.
    

So, in simple terms, multi-tenancy in Azure App Service is like having different companies (tenants) sharing the same building (environment) but with each having its own secure space, resources, and ability to customize.