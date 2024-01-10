
 Azure Policy also evaluates and monitors all current VMs in your environment, including VMs that were created before the policy was created.
- For example, if all resources in a certain resource group should be tagged with *AppName* tag and a value of *"SpecialOrders"* Azure Policy will automatically apply that tag if it is missing. 
- However, you still retain full control of your environment. If you have a specific resource that you don’t want Azure Policy to automatically fix, <mark style="background: #FF5582A6;">you can flag</mark> that resource as an exception – and the policy won’t automatically fix that resource.

---

# Policy initiatives

- ! grouping related policies together.
- policy definitions to help track your compliance state for a larger goal.
- @ For example, Azure Policy includes an initiative named <u>Enable Monitoring</u> in Azure Security Center. Its goal is to monitor all available security recommendations for all Azure resource types in Azure Security Center.