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

---
## Installing Rsyslog


* installing rsyslog daemon.
```bash
sudo apt-get install rsyslog
```

* check the status after installation
```bash
sudo systemctl status rsyslog
```

---
- Pricing in Sentinel.
- Rsyslog / log forwarding to Sentinel.
- Tables migration in Log analytic workspace.
- Log management in Sentinel.
- Restoring Archival logs in Sentinel.
- Threat Intelligence in Sentinel.
- UEBA in Sentinel.

