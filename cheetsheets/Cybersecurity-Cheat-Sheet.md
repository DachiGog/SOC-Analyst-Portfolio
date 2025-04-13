# 🛡️ Cybersecurity Cheat Sheet

_A comprehensive resource for offensive security, pentesters, red teamers, and students._

---

## 📚 Table of Contents

- [Acronyms & Terminologies](#acronyms--terminologies)
- [OWASP Top 10 (2023)](#owasp-top-10-2023)
- [OSI Model](#osi-model)
- [Common Attacks](#common-attacks)
- [Common Ports](#common-ports)
- [Tools & Suites](#tools--suites)
- [HTTP Methods & Status Codes](#http-methods--status-codes)
- [Payload Examples](#payload-examples)
- [Encoding & Obfuscation](#encoding--obfuscation)
- [Recon Techniques](#recon-techniques)
- [MITRE ATT&CK](#mitre-attck)
- [References & Resources](#references--resources)

---

## 🧩 Acronyms & Terminologies

| Acronym | Full Form                          | Description |
|---------|------------------------------------|-------------|
| APT     | Advanced Persistent Threat         | Long-term targeted attack |
| CVE     | Common Vulnerabilities & Exposures | Public ID for known vulnerabilities |
| CWE     | Common Weakness Enumeration        | Categorization of software flaws |
| XSS     | Cross-Site Scripting               | Injecting malicious JS code |
| CSRF    | Cross-Site Request Forgery         | Exploits user session trust |
| LFI     | Local File Inclusion               | Includes local server files |
| RFI     | Remote File Inclusion              | Includes remote files via input |
| IDOR    | Insecure Direct Object Reference   | Broken access control |
| SSRF    | Server-Side Request Forgery        | Server performs unintended requests |
| MITM    | Man-In-The-Middle                  | Interception of communication |
| JWT     | JSON Web Token                     | Token format for authentication |
| ACL     | Access Control List                | Rules for user access rights |

---

## 🔐 OWASP Top 10 (2023)

| #  | Title                              | Description                          |
|----|------------------------------------|--------------------------------------|
| 1  | Broken Access Control              | IDOR, forced browsing, privilege escalation |
| 2  | Cryptographic Failures             | Weak or no encryption                |
| 3  | Injection                          | SQL, NoSQL, OS command injection     |
| 4  | Insecure Design                    | Weak architecture or security flaws  |
| 5  | Security Misconfiguration          | Default creds, debug info exposed    |
| 6  | Vulnerable & Outdated Components   | Unpatched systems, libraries         |
| 7  | Identification & Auth Failures     | Broken login or session management   |
| 8  | Software & Data Integrity Failures | Dependency confusion, CI/CD flaws    |
| 9  | Security Logging & Monitoring Failures | Insufficient detection, alerts     |
| 10 | SSRF                               | Requests from server to internal systems |

---

## 📡 OSI Model

