---
semester: 1
ects: 3
type: compulsory
tags:
  - cybersecurity
  - ethical-hacking
  - course
  - semester-1
---
# Threat Assessment Tools

This note covers specific tools used for system-level security assessment and defense.

## Host-Based Security Tools

These tools protect individual devices (hosts) like servers or laptops by monitoring activity _on_ the device itself.

- **Host-Based Security System (HBSS):** A suite of tools deployed on a host to provide a layered defense (e.g., firewall, antivirus, HIDS).
- **Host-Based Intrusion Detection System (HIDS):** A system that monitors a host for signs of malicious activity or policy violations. It often works by monitoring logs or checking for file changes.
- **Host-Based Firewalls:** Software that controls network traffic in and out of a single machine.

## System Auditing & Monitoring Tools

These are open-source tools commonly used for auditing and real-time threat detection.

### Lynis

- **What it is:** A security auditing tool for Unix-based systems.
- **What it does:** It audits the system's security posture, checking for file permissions, user accounts, kernel settings, firewall rules, and more.
- **Command:** `lynis audit system`

### OSSEC

- **What it is:** A popular open-source Host-Based Intrusion Detection System (HIDS).
- **What it does:** It monitors system logs, detects file integrity changes (FIM), and can perform active responses based on rules.

### Sysdig Falco

- **What it is:** A real-time threat detection tool, often used for containers and cloud-native environments.
- **What it does:** It detects abnormal behavior by monitoring system calls. For example, it can trigger an alert if a shell is opened inside a running container.