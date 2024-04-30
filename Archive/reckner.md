---
title: Archive
date: 2024-04-30
resources: 
tags:
---
# The rpcgssd service should be disabled.

**Description:**

The `rpcgssd` service is related to the NFS (Network File System),
%%
And is used for RPC (Remote Procedure Call) security with GSSAPI (Generic Security Services Application Program Interface),
%%
which often involves Kerberos authentication.

**Impact:**

- If your system **does not require NFS** or you are **not using Kerberos for authentication**, leaving `rpcgssd` enabled could pose unnecessary security risks. Unnecessary services can be potential entry points for attackers.
- Disabling it could slightly reduce the system’s resource usage.

**Solution:**

- `rpcgssd` is considered a static service that always starts during boot and cannot be simply disabled.
- If you want to prevent `rpcgssd` from starting during boot, you should **mask** the service.

```bash
systemctl mask rpcgssd.service
```

- For unmasking it
```bash
systemctl unmask rpcgssd.service
```

---
# Ensure SSH Idle Timeout Interval is configured.

**Description:**

SSH (Secure Shell) idle timeout intervals are a security feature that automatically terminates an SSH session after a specified period of inactivity.

**Impact:**

Without a timeout, an unauthorized user could potentially access another user’s SSH session if they leave their computer unattended and unlocked, as the session would remain active indefinitely.

**Solution:**

You can configure the SSH Idle Timeout Interval by setting the `ClientAliveInterval` and `ClientAliveCountMax` parameters in your SSH daemon configuration file (`/etc/ssh/sshd_config`).

```bash
sudo nano /etc/ssh/sshd_config
```

```bash
ClientAliveInterval 900  # No greater than 900 seconds
ClientAliveCountMax 0
```

```bash
sudo systemctl restart sshd
```

---
# Ensure only approved MAC algorithms are used

**Description:**



**Impact:**

Leads to security vulnerabilities

Unapproved or weak MAC algorithms can be exploited in SSH attacks, potentially allowing an attacker to capture sensitive data or credentials.

**Solution:**