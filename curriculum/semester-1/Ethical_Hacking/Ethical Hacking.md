---
semester: 1
ects: 3
type: compulsory
tags:
  - "#cybersecurity"
  - ethical-hacking
  - course
  - semester-1
---
# 🧑‍💻 Ethical Hacking

This note serves as the introduction to the Ethical Hacking module. Ethical Hacking is the authorized practice of testing a computer system, network, or application to identify security vulnerabilities before a malicious attacker can. The goal is to improve the system's security by fixing these flaws.

## Module Notes (Index)

* [[Threats, Vulnerabilities, and Attacks]]
* [[Risk and Threat Modeling]]
* [[Ethical Hacking Principles and ROE]]
* [[Red Team vs Blue Team]]
* [[OS Security and Hardening]]
* [[Reconnaissance and Enumeration]]
* [[Threat Assessment Tools]]

---

## Importance of Ethical Hacking

Ethical hacking is a crucial process for several reasons:

* **Protecting Data:** It helps identify vulnerabilities that could lead to data breaches, protecting personal, financial, or confidential business data.
* **Preventing Attacks:** By finding and fixing weaknesses, organizations can minimize the risk and damage from malicious hackers.
* **Enhancing Security:** It provides a comprehensive assessment of security measures and highlights areas for improvement.
* **Compliance:** It helps organizations meet legal and regulatory requirements, reducing the risk of legal liability.

## Cyber Security vs. Ethical Hacking

While related, the two fields have different primary goals:

| Aspect | Cyber Security (Defense) | Ethical Hacking (Offense) |
| :--- | :--- | :--- |
| **Definition** | Protecting systems and data from threats. | Finding vulnerabilities to prevent exploitation. |
| **Primary Goal**| Defense and prevention. | Identifying weaknesses. |
| **Approach** | Holistic, covering all security aspects. | Offensive, simulating attacks. |
| **Focus Area** | Long-term security management. | Short-term testing and vulnerability detection. |

## Types of Ethical Hacking (Testing Models)

Testing models are defined by the amount of knowledge the ethical hacker has about the target system:

* **White Box Testing:** The tester has **complete knowledge** of the system, including source code, design, and architecture.
* **Black Box Testing:** The tester has **no knowledge** of the system. They approach it as a real-world attacker would.
* **Gray Box Testing:** The tester has **partial knowledge** of the system, such as user-level credentials or some architectural diagrams.

## The 5 Steps of Ethical Hacking

Ethical hacking follows a structured process, often broken into five phases:

1.  **Reconnaissance:** Gathering information about the target system using various tools and techniques. (See [[Reconnaissance and Enumeration]])
2.  **Scanning:** Actively probing the target to find open ports, running services, and potential vulnerabilities.
3.  **Gaining Access:** Attempting to exploit identified vulnerabilities to gain unauthorized access.
4.  **Maintaining Access:** Simulating an attacker's goal of remaining hidden in the system to test how long they can maintain access.
5.  **Covering Tracks:** Cleaning up logs and removing any tools to test the system's logging and monitoring capabilities.

## Challenges in Ethical Hacking

* **Knowledge & Skills:** The field requires a strong technical background and is constantly evolving.
* **Cost:** Specialized tools and resources can be expensive to purchase and maintain.
* **Legal Issues:** Testers must be careful not to cross legal or ethical lines and must stay compliant with laws.
* **Time Constraints:** Testing large, complex systems can be very time-consuming.