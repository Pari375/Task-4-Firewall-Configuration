# Firewall Configuration Report

## 1. Overview

This report documents the configuration and testing of firewall rules using UFW (Uncomplicated Firewall) on a Linux system.

The objective was to understand how firewall rules control network traffic by allowing or blocking communication through specific ports.

---

## 2. Environment

| Component | Details |
|----------|---------|
| Operating System | Kali Linux |
| Firewall Tool | UFW (Uncomplicated Firewall) |
| Test Rule | Block Telnet Traffic |
| Blocked Port | TCP Port 23 |
| Allowed Port | TCP Port 22 (SSH) |

---

## 3. Initial Firewall Status Check

The current firewall configuration was checked using:

```bash
sudo ufw status verbose
```

This command displays:
- Firewall status
- Default policies
- Existing allow/deny rules

---

## 4. Allow SSH Traffic

Before enabling the firewall, SSH traffic was allowed to prevent accidental remote access issues.

Command used:

```bash
sudo ufw allow 22/tcp
```

### Purpose

Port 22 is used by SSH (Secure Shell), which allows secure remote administration of Linux systems.

Allowing SSH ensures authorized remote connections remain accessible.

---

## 5. Enable Firewall

The firewall was enabled using:

```bash
sudo ufw enable
```

After enabling, active rules were verified using:

```bash
sudo ufw status numbered
```

---

## 6. Blocking Telnet Traffic

A rule was created to block inbound Telnet traffic.

Command:

```bash
sudo ufw deny 23/tcp
```

### Reason for Blocking Port 23

Telnet is considered insecure because it sends data, including usernames and passwords, in plaintext.

Attackers can intercept Telnet communication and steal sensitive information.

SSH is recommended as a secure replacement.

---

## 7. Firewall Rule Verification

The configured firewall rules were listed using:

```bash
sudo ufw status numbered
```

Applied rules:

| Port | Action | Protocol |
|----|----|----|
| 22 | Allow | TCP |
| 23 | Deny | TCP |

---

## 8. Testing the Firewall Rule

The Telnet block rule was tested using:

```bash
telnet localhost 23
```

The connection attempt failed, confirming that the firewall successfully blocked traffic on port 23.

---

## 9. Removing Test Rule

After testing, the temporary blocking rule was removed.

Rules were listed:

```bash
sudo ufw status numbered
```

The deny rule was removed using:

```bash
sudo ufw delete <rule_number>
```

---

## 10. How Firewall Filtering Works

A firewall monitors incoming and outgoing network traffic and compares it against predefined rules.

Based on these rules, traffic can be:

- Allowed
- Blocked
- Logged

Firewalls reduce security risks by limiting unnecessary network exposure and preventing unauthorized access.

---

## Conclusion

The firewall configuration task successfully demonstrated basic traffic filtering using UFW. Rules were created to allow trusted services and block insecure services. This exercise provided practical experience with firewall management, port security, and network traffic control.