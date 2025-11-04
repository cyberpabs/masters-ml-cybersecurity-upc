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
# OS Security and Hardening

This note covers the internal structure of operating systems and how to secure them.

## OS Architecture Models

- **Monolithic Architecture:** All OS components (file systems, memory management, drivers) run together in one large kernel in privileged mode.
    - **Pros:** Fast performance, fast system calls.
    - **Cons:** Less secure; if one part fails, the whole system can crash. It's also large and complex.

- **Microkernel Architecture:** The kernel is minimal, only containing the most basic components (e.g., IPC, basic scheduling). Other services like drivers and file systems run in user mode.    
    - **Pros:** More stable and secure (fault isolation), modular, and easier to maintain.
    - **Cons:** Slower message passing between components, which can limit performance.

## Kernel vs. User Space

Modern operating systems separate memory into two distinct areas to protect the core OS:

- **Kernel Space:** The privileged area where the OS kernel runs. It has direct access to all hardware and memory.
- **User Space:** The unprivileged area where applications run. They must ask the kernel for access to hardware or other resources via **system calls**.

This separation (privilege separation) is a fundamental security primitive.

## Access Control

- **File Permissions:** Rules that control who can **read, write, or execute** files. Classic Linux permissions use three roles: **owner, group, and others**.
- **ACLs (Access Control Lists):** Go beyond basic permissions by allowing **fine-grained rules** for specific users or groups on a per-file basis.

## System Hardening Strategies

Hardening is the process of reducing a system's attack surface. Key strategies include:

1. **Disabling Unnecessary Services:** Reducing the number of running services that could be exploited.
2. **Implementing Strong Access Controls:** Using ACLs and the principle of least privilege.
3. **Patch Management:** Regularly updating systems to fix known vulnerabilities.
4. **Secure Configurations:** Applying secure settings, not using defaults.
5. **Securing User Accounts:** Enforcing strong password policies.
6. **Logging and Monitoring:** Actively logging and monitoring system activity.

## Common Exploitation Techniques

Attackers often target OS-level flaws to gain control.

- **Buffer Overflows:** Occurs when a program writes more data to a buffer (a temporary storage area) than it can hold. This can overwrite adjacent memory, allowing an attacker to inject and execute their own code.
- **TOCTOU (Time-of-Check to Time-of-Use) Race Conditions:** A flaw where a program checks a resource's state (e.g., "does this file exist?") but the state changes _before_ the program uses that resource. An attacker can exploit this tiny gap to, for example, swap a legitimate file for a malicious one.
- **Privilege Escalation:** An attack that exploits a bug or misconfiguration to gain elevated access (e.g., from a regular user to an administrator/root).

### Common Entry Vectors

- **Poorly Written Drivers:** Drivers often run with high kernel privileges, making them a prime target for buffer overflows or other flaws.
- **Exposed System Calls:** Attackers look for system calls that lack proper input validation, which can be exploited.