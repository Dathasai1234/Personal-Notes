---
title: Sentinel
date: 2024-06-19
resources: 
tags:
---
## Rsyslog

- Accept inputs from a wide variety of sources.
- Transform them.
- Output the results to diverse destinations.

---
## Syslog

- Standard protocol for sending or receiving messaged between devices or applications over a network.
- Have a predefined structure that consists
	- Priority.
	- Timestamp.
	- Hostname.
	- Application name.
	- Process ID.
	- Message text.
- Can be sent over TCP,UDP or TLS, depending on the configuration and the security requirements.
- The log data is stored in **Syslog** table
- The Syslog daemon on your device should forward messages to the **Log Analytics agent** (formerly known as the OMS agent) on UDP port 25224.[^1]

---
## CEF

- Common Event Format.
- A vendor neutral format for logging data from network and security devices and applications, suchas.
	- Firewalls.
	- Routers
	- Detection and response solutions.
	- Intrusion detection systems.
	- Web servers.
- CEF is an extention of Syslog.
- It was developed for SIEM solutions.
- CEF messages have a standard header that contains information such as.
	- Device vendor.
	- Device product.
	- Device version.
	- Event class 
	- Event security.
	- Event ID.
- CEF messages also have a multiple number of extensions that provide more details about the event.
	- Source and destination IP addresses.
	- Username.
	- Filenames.
	- Action taken.
- The log data is stored in the **CommonSecurityLog** table
- ! We can correlate a CEF alert with relevant Syslog event to understand the broader context of an incident.

---
- ! Recommendation
	- If your primary focus is security monitoring and threat detection, consider using CEF. It provides better context and consistency.
	- If you need to collect logs from a wide variety of sources (including non-security devices), Syslog might be more practical.

---
## Architecture of syslog forwarder VM

![[Pasted image 20240619211701.png]]

![[Pasted image 20240619211704.png]]

---
## Syslog Collector setup - Youtube

- The default flow of syslog is UDP. To get logs effectively, we can use TCP.
- Process of setup
```bash
apt install rsyslog

netstat -ano # that will show if we are listening to 514 port and if it's not

nano /etc/rsyslog.conf
```

![[Pasted image 20240619214532.png | 400]] 

Ctrl+x = move out of the console and Y for saving.


---
[^1]: The OMS agent listens for Syslog messages on the local client at **port 25224**. The configuration file for the Syslog daemon forwards Syslog messages sent from application to this port where they are collected by Log Analytics.