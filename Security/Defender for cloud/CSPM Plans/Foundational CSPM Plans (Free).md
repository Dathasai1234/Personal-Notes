# Foundational CSPM

## Inventory

- Inventory of all Azure resources connected to Defender for Cloud
- Can be leveraged to answer questions such as:
	- Which of my subscriptions have outstanding recommendations?
	- Which of my machines with the tag 'Critical' are missing the Azure Monitor Agent?
	- Which machines in a specific resource group have a known vulnerability (using A CVE number)?

- Features:
	- Filtering the resources, based on recommendations, ...
	- Total resources
	- Unhealthy resources
	- Unmonitored resources
	- Unreg subs
	- Can add non-azure resources
	- Open Query and interact using KQL query
	- Download as CSV report
	- Recommendations for a specific resource
	- Monitoring agent installed or not
	- Defender for cloud is On or Off for a resource.

---
## Security Recommendations

- Defender for Cloud assesses your resources against security Controls in Azure, AWS and GCP
- Based on that assessment, security recommendations are provided
- Recommendations are implemented via Azure Policy

- Features
	- All recommen
	- Severity of recommendations (High, medium, low)
	- Resource health (Unhealthy, Healthy, Not applicable)
		- Unhealthy : A resource with an active recommendation
		- Healthy : A resource with no active recommendation
	- Status of the recommendation (completed or not)
	- Overdue recommendations
	- Recommendations drilling down for you resources using filters
	- Lightning bolt - Fix is available

---
## Secure Score

Entire purpose of Ss is to provide a number from 0 - 100, and this number tells you how secure you are for your various resources

![[Pasted image 20240131131940.png | 400]]

List of recomm that are associated with the MS secure score
- Features:
	- Recommendations which can increase the SS
		- Domains
			- Like enabling MFA
			- Secure Management Ports
			- Apply System Updates...
		- Have multiple recomm for a single domain
	- Max score and current score for a domain (progress bar)
	- Unhealthy resources categorized on domains

---
## Workbooks

Can also be used in Sentinel and Azure Monitor.

- Purposes - Can be used for
	- Data Visualization
	- Create Dashboards
- Workbooks allow for data visualization and dashboarding
- Workbooks can be built from scratch or customized
- Defender for Cloud includes prebuilt workbooks, such as:
	- Secure Score over Time
	- Vulnerability Assessment Findings
	- DevOps Security
	- System Updates
<br>
- Can be created from scratch or use pre-built workbooks
- Can use *KQL Query* to create dashboards and visualizations
- Also use *Add metric* option, for simplistic approach to create dashboards and visualizations using dropdowns.

![[Pasted image 20240131134232.png | 200]]

---
## Data Exporting

To export alerts and recommendations or vulnerability to other 3rd party tools.

You can stream the alerts and recommendations to the services so that the respective teams can get the expected alerts.

If you don't want to use Sentinel as a *Security information and event management (SIEM)* and want to use other SIEM solution, then you can leverage this feature of CSPM.

- ! We can Export the data to an EventHub or another log-analytic workspace
- There are built-in Azure tools for ensuring you can view your alert Data in all of the most popular solutions in use today, including:
	- Microsoft Sentinel
	- Splunk Enterprise and Splunk Cloud
	- IBM's QRadar
	- ServiceNow
	- ArcSight
	- Power Bl
	- Palo Alto Networks

- Features:
	- Export it to Event-Hub
	- Exported Date-Types
		- Which security *recomm* to export or all
		- *Recomm severity* (low, med, high)
		- *Secure score* export (all, Overall Score, Control Score)
			- Eg - only MFA Secure Score
		- Export *alerts* based on severity
		- Regulatory Compliance - ISO or Default - Azure - Sec - Benchmark
	- Frequency
		- Streaming Updates (real-time streaming)
		- Snapshots (specific snapshot).

---
## Remediations

Can be done manually and have another option which azure take cares to remediate the recomm, (when you click on Quick fix).

- Security recommendations should be remediated frequently
- Defender for Cloud always explains how to do this in general
- There is also a quick fix option available. Be careful if:
	- You manage resources with laC (you will introduce so-called *drift*)
	- You don't know the workload as you can heavily impact it by applying a fix Automatically

There will be a period called Freshness period which will tale 30 minutes to remove the recommendation after you click on *quick fix*

---
## Microsoft Cloud Security Benchmark

	Cloud Security > regulatory compliance

Renamed from
Azure Security Benchmark
⬇️
Microsoft Cloud Security Benchmark.

- Benchmark provides best practices and recommendations for your resources
- Control Domains
	- Network Security
	- Identity Management
	- Privileged Access
	- Data Protection
	- Asset Management
	- Logging and Threat Detection
	- Incident Response
	- Posture and Vulnerability Management
	- Endpoint Security
	- Backup and recovery
	- DevOps Security
	- Governance and Strategy

Lot of them are invented by Microsoft but. It also had a look at the most prominent industry benchmarks, like 

- CIS benchmarks
- NIST
- PCI
- DSS
- AWS well-Architected framework

<img src = "https://learn.microsoft.com/en-us/azure/defender-for-cloud/media/concept-regulatory-compliance/microsoft-security-benchmark.png"/>

Microsoft took and grouped under an umbrella, which is now called Microsoft Cloud Security Benchmark.

You can leverage the benchmark to identify recomm in defender for cloud and then also to address them accordingly.

- ! These domains have all the controls and these controls have sub-controls
![[Pasted image 20240131152745.png]]
