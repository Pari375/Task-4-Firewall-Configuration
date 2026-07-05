# Task 4: Setup and Use a Firewall on Linux

## Overview

This project demonstrates basic firewall configuration and traffic filtering using UFW (Uncomplicated Firewall) on Linux.

Firewall rules were created, tested, and managed to understand how network traffic can be controlled by allowing or blocking specific ports.

---

## Objective

The objective of this task was to:

- Configure basic firewall rules.
- List existing firewall configurations.
- Allow trusted network traffic.
- Block insecure services.
- Test firewall behavior.
- Understand how firewalls filter traffic.

---

## Tools Used

- Kali Linux
- UFW (Uncomplicated Firewall)
- Terminal

---

## Repository Structure

```
Task-4-Firewall-Configuration/
│
├── README.md
├── firewall_report.md
└── screenshots/
    ├── 01_initial_firewall_status.png
    ├── 02_firewall_rules.png
    └── 03_block_test.png
```

---

## Steps Performed

### 1. Checked Existing Firewall Rules

The current firewall status and existing rules were checked using:

```bash
sudo ufw status verbose
```

---

### 2. Allowed SSH Traffic

SSH traffic was allowed through TCP port 22:

```bash
sudo ufw allow 22/tcp
```

This ensures secure remote access remains available.

---

### 3. Enabled Firewall

UFW firewall protection was enabled:

```bash
sudo ufw enable
```

---

### 4. Blocked Telnet Traffic

Inbound Telnet traffic was blocked:

```bash
sudo ufw deny 23/tcp
```

Port 23 was selected because Telnet transmits data without encryption and is considered insecure.

---

### 5. Tested Firewall Rule

The blocking rule was tested using:

```bash
telnet localhost 23
```

The connection attempt was blocked, confirming that the firewall rule was working correctly.

---

### 6. Removed Test Rule

After testing, the temporary firewall rule was removed:

```bash
sudo ufw delete <rule_number>
```

---

## Key Learnings

Through this task, I learned:

- How firewall rules control network communication.
- Difference between allowing and denying traffic.
- Importance of securing exposed ports.
- Why insecure protocols like Telnet should be blocked.
- Basic Linux firewall administration using UFW.

---

## Conclusion

The task successfully demonstrated firewall rule creation, verification, testing, and removal using UFW. Proper firewall configuration helps reduce attack surfaces and improves overall system security.