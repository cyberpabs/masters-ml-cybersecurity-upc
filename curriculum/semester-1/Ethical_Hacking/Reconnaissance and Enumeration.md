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
# Reconnaissance and Enumeration

Reconnaissance (or "recon") is the first and most crucial phase of an attack. It involves gathering as much information as possible about a target _before_ launching an attack.

## Reconnaissance Types

Recon is categorized by how much the attacker interacts with the target.

### Passive Reconnaissance

Gathering intelligence without directly interacting with the target's systems. The goal is to remain undetected.

- **Methods:** Using publicly available information (OSINT - Open-Source Intelligence)
- **Tools/Techniques:**
    - **WHOIS:** Looking up domain registration records.
    - **Google Dorking:** Using advanced Google search operators to find sensitive files or login pages.
    - **Shodan:** A search engine for internet-connected devices (e.g., webcams, servers).
    - **Social Media:** Harvesting information about employees or technology.
    - **DNS Lookups:** Using `dig` or `nslookup` to find domain information.

### Active Reconnaissance

Directly engaging with the target system to gather information. This is "noisier" and risks detection.

- **Methods:** Sending packets to the target system to see how it responds.
- **Tools/Techniques:**
    - **Nmap:** A powerful port scanner used to discover open ports and running services.
    - **Netcat:** A versatile networking utility used for reading/writing to network connections. Can be used for "banner grabbing."
    - **Banner Grabbing:** Connecting to a service (like SSH or FTP) to read the "banner," which often reveals the exact software version (e.g., `nmap -sV`).

## Target Enumeration Techniques

Enumeration is the process of extracting detailed information from a target system, such as:
- Port Scanning
- Service Version Detection
- OS Fingerprinting
- DNS Enumeration
- User Enumeration (e.g., NetBIOS, LDAP, Active Directory)
- Vulnerability Scanning

### Common Enumeration Tools

- **Nmap**
- **Enum4linux** (for Windows/Samba enumeration)
- **SuperScan**
- **Hydra** (for brute-forcing logins)

## Core Networking Concepts (OSI & TCP/IP)

Understanding network protocols is essential for reconnaissance.

- **OSI Model:** A 7-layer conceptual model (Physical, Data Link, Network, Transport, Session, Presentation, Application).
- **TCP/IP Model:** A 4-layer model used by the internet (Network Access, Internet, Transport, Application).
- **TCP (Transmission Control Protocol):** A **connection-oriented** protocol. It's reliable and performs a "three-way handshake" (SYN, SYN-ACK, ACK) to establish a connection before sending data.
- **UDP (User Datagram Protocol):** A **connectionless** protocol. It's faster but unreliable—it just sends packets without checking if they arrive (e.g., used for DNS, video streaming).