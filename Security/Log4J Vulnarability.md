---
title: Security
date: 2024-01-18
resource_2: https://builtin.com/cybersecurity/log4j-vulerability-explained
minecraft alert: https://www.minecraft.net/en-us/article/important-message--security-vulnerability-java-edition
tags:
---
- #Log4J is a logging library for java.
	- an open-source logging framework maintained by Apache.

> [!info] 
> It’s used to log messages within software and has the ability to communicate with other services on a system. This communication functionality is where the vulnerability exists, providing an opening for an attacker to inject malicious code into the logs so it can be executed on the system.

- After its discovery, security researchers saw millions of attempted exploits, many of which turned into successful denial-of-service (DoS) attacks.
<br>
- The vulnerability was first discovered in a version of the game _Minecraft_.
- Malicious individuals learned that the game’s chat was being logged using Log4j.
- If they entered malicious code into the chat, it led to remote code execution (RCE).
- [Remote code execution](https://www.geeksforgeeks.org/what-is-remote-code-execution-rce/) is a type of cyberattack that allows an individual to execute code on a backend system, remotely.
<br>
- It didn’t take long for official ==POC (proof of concepts)==[^1] code to surface on GitHub, an open-source coding community where members can share and collaborate on coding projects. 
- The software community uses it to develop programs. 
- For cybersecurity experts, however, it’s used to share scripts and programs related to securing or exploiting various systems or vulnerabilities. 
- This includes **POC code**, or **exploit code**, typically with instructions, that *publicizes how to exploit a specific vulnerability*.

- In the case of Log4j, [a GitHub user published a Log4j POC for LDAP](https://github.com/kozmer/log4j-shell-poc) (Lightweight Directory Access Protocol) remote code execution. 
- If you recall, RCE attacks result in malicious code being executed on a remote system, and the exploit is leveraging the [LDAP](https://www.securew2.com/blog/ldap-explained) service, which is a protocol used for cross-platform directory services authentication. 
- In simpler terms, it’s what enables a remote directory (typically Microsoft Active Directory) to be searched and used for authentication purposes to an internal service.
<br>
- Performing the exploit
	- To perform the exploit using the popular POC code on GitHub, 
	- ! all an attacker has to do is run the provided script on their system to deploy an HTTP server and fake LDAP server, then inject the [crafted malicious payload](https://www.malwarebytes.com/glossary/payload) into a text field on a vulnerable platform. This can be within a chat, like in the <u>_Minecraft_ exploit, or as simple as pasting the command into the username field of a login form with a random password.</u>
	- You might be wondering, “What’s so special about the crafted payload?” 
	- The payload is ultimately what exploits the Log4j vulnerability. 
	- ! It does so by using JNDI, Java Naming and Directory Interface, a feature that enables a user to fetch and load Java objects from a server. 
	- Although this is a secure functionality, the Log4j flaw allows an attacker to input their own JNDI lookups, where they then direct the server to their fake LDAP server. 
	- From here, the attacker now has control of the remote system and can execute malware, exfiltrate sensitive information like passwords, and more.


[^1]: POC code stands for "proof of concept" code. It's a small-scale, experimental piece of software designed to demonstrate the feasibility of an idea or to test a theory. It's like building a miniature model of a bridge before constructing the full-sized version to ensure it's structurally sound.