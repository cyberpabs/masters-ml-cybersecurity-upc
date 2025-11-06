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
# Threats, Vulnerabilities, and Attacks

Understanding the fundamental concepts of threats, vulnerabilities, and attacks is essential for cybersecurity.

## Core Definitions

* **Threat Actor vs. Threat Agent:**
    * **Threat Actor:** The **person or group** with the intent to cause harm (e.g., cybercriminals, nation-states, insiders).
    * **Threat Agent:** The **tool or method** used by the actor to carry out the attack (e.g., malware, phishing email).
* **Weakness vs. Vulnerability:**
    * **Weakness:** An underlying **flaw or deficiency** in a system or process that *increases risk* but may not be directly exploitable (e.g., weak policies, no training).
    * **Vulnerability:** A **specific, exploitable weakness** that a threat actor can use to compromise a system (e.g., unpatched software, an open port).
* **Attack vs. Exploit vs. Breach:**
    * **Attack:** The **attempt** by a threat actor to compromise a system. It doesn't always succeed.
    * **Exploit:** The **tool or code** that takes advantage of a specific vulnerability.
    * **Breach:** The **result of a successful attack** where unauthorized access is gained or data is exposed.

## Attack Taxonomy

This is a structured classification of cyberattacks, often broken down by:

* **Attack Method/Vector:** How the attack is delivered (phishing, malware).
* **Target:** What is being attacked (network, application, data).
* **Impact:** The intended damage (data theft, service outage).
* **Motivation:** The reason for the attack (financial gain, espionage).

### Common Attack Patterns

* **Injection (e.g., SQLi, XSS):** Injecting malicious code into an application.
* **Denial of Service (DoS):** Overloading a system to make it inaccessible.
* **Social Engineering:** Manipulating people to give up confidential information.
* **Supply Chain Attacks:** Targeting a trusted third-party software or service.
* **Insider Threats:** Attacks from within an organization (malicious or accidental).

## Vulnerability Classification Systems

* **CVE (Common Vulnerabilities and Exposures):** A list of **specific, publicly known vulnerabilities** in software and hardware. Each has a unique ID (e.g., CVE-2021-44228).
* **CWE (Common Weakness Enumeration):** A catalog of **types of weaknesses** (the root causes) that can lead to vulnerabilities (e.g., CWE-79: "Improper Neutralization of Input," which leads to XSS).
* **CAPEC (Common Attack Pattern Enumeration and Classification):** A library describing **common attack patterns** and how attackers exploit weaknesses.

> **How they work together:** A **CVE** (the specific instance) maps to a **CWE** (the underlying weakness), which can be exploited using a **CAPEC** (the attack method).

## Severity Scoring (CVSS)

The **Common Vulnerability Scoring System (CVSS)** is a standard for rating the severity of vulnerabilities on a scale from 0 to 10. The score is calculated using three metric groups:

1.  **Base:** The inherent qualities of the vulnerability (e.g., attack vector, complexity, impact).
2.  **Temporal:** Factors that change over time (e.g., availability of an exploit or a patch).
3.  **Environmental:** Factors unique to a specific organization's environment.

## OWASP Top Ten

The OWASP Top Ten is a widely recognized document that lists the ten most critical web application security risks.

1.  **A01: Broken Access Control:** Users can access data or functions outside their permissions.
2.  **A02: Cryptographic Failures:** Weak or improperly used encryption.
3.  **A03: Injection:** (e.g., SQL, NoSQL, XSS, OS).
4.  **A04: Insecure Design:** Flaws in the fundamental architecture.
5.  **A05: Security Misconfiguration:** Unsecure default settings, open S3 buckets, etc..
6.  **A06: Vulnerable and Outdated Components:** Using third-party libraries with known vulnerabilities.
7.  **A07: Identification and Authentication Failures:** Poor session management, weak passwords.
8.  **A08: Software and Data Integrity Failures:** Issues with insecure updates or CI/CD pipelines.
9.  **A09: Security Logging and Monitoring Failures:** Inadequate logging to detect breaches.
10. **A10: Server-Side Request Forgery (SSRF):** Forcing a server to make requests on an attacker's behalf.