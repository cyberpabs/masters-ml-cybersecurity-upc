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
# Risk and Threat Modeling

Risk and threat modeling are crucial proactive processes in cybersecurity.

## Risk Modeling vs. Threat Modeling

- **Threat Modeling:** A **proactive, detailed process** that focuses on a _specific system or application_ to identify possible threats and vulnerabilities, usually during the development phase. It asks, "What could go wrong here, and how can we stop it?".

- **Risk Modeling (Risk Assessment):** A **broader, high-level view** across the _entire organization_ to evaluate potential risks, their impact, and their likelihood. It helps set priorities and asks, "How bad would it be if X happened, and what's most important to fix first?".    

## Threat Modeling Process

A typical threat modeling process involves several steps:

1. **Define Scope & Objectives**
2. **Diagram the System** (e.g., Data Flow Diagrams)
3. **Identify Threats** (using frameworks like STRIDE)
4. **Analyze & Prioritize Risks** (using frameworks like DREAD)
5. **Identify Mitigations**
6. **Review & Iterate**

## Threat Modeling Frameworks

Frameworks provide structured approaches to identifying and assessing threats.

### STRIDE

Developed by Microsoft, STRIDE is a mnemonic for classifying six categories of threats:

- **S**poofing: Impersonating another user or device.
- **T**ampering: Unauthorized alteration of data.
- **R**epudiation: Denying an action was taken.
- **I**nformation Disclosure: Unauthorized access to confidential information.
- **D**enial of Service (DoS): Disrupting service for legitimate users.
- **E**levation of Privilege: Gaining unauthorized access to higher permissions.

### DREAD

DREAD is a framework used for risk-rating and prioritizing threats. It was dropped by Microsoft for being too subjective but is still used by other organizations.

- **D**amage Potential: How much damage would be caused?
- **R**eproducibility: How easy is it to reproduce the attack?
- **E**xploitability: How easy is it to launch the attack?
- **A**ffected Users: How many users would be impacted?
- **D**iscoverability: How easy is it to find the vulnerability?

### Other Popular Frameworks

- **PASTA** (Process for Attack Simulation and Threat Analysis)
- **OWASP Top Ten**
- **Attack Trees**
- **CIA Method** (Confidentiality, Integrity, Availability)

## Attack Surface Analysis

This involves mapping all the services and interfaces that are exposed to untrusted users. The goal is to identify all possible entry points for an attacker.

Common elements include:
- **Physical Access:** Premises, loss/theft of devices.
- **Network:** Open ports, protocols, firewalls, IP addresses.
- **Software:** Web applications, operating systems, cloud storage.
- **Human:** Credentials, data leaks, DNS registration.