# 🛡️ Cybersecurity Cheat Sheet


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

- [OSI Model](../images/WHAT-IS-OSI-MODEL-7-LAYERS-EXPLAINED.jpg)

---

## 🧪 Common Attacks

| Type               | Description                        | Example Payload                        |
|--------------------|------------------------------------|----------------------------------------|
| SQL Injection       | Code injection into SQL queries   | `' OR '1'='1 --`                        |
| XSS (Reflected)     | JS Injection via user input       | `<script>alert(1)</script>`            |
| CSRF                | Triggers actions via GET/POST     | `<img src="http://site/delete?u=1">`   |
| Command Injection   | Executes shell commands           | `; whoami`                              |
| XXE                 | XML parser attack                 | `<!ENTITY xxe SYSTEM "file:///etc/passwd">` |
| Open Redirect       | Redirects to external sites       | `?redirect=https://evil.com`           |

---

## 📦 Common Ports

| Port | Protocol | Service        |
|------|----------|----------------|
| 21   | TCP      | FTP            |
| 22   | TCP      | SSH            |
| 23   | TCP      | Telnet         |
| 25   | TCP      | SMTP           |
| 53   | UDP/TCP  | DNS            |
| 80   | TCP      | HTTP           |
| 110  | TCP      | POP3           |
| 139  | TCP      | NetBIOS        |
| 143  | TCP      | IMAP           |
| 443  | TCP      | HTTPS          |
| 445  | TCP      | SMB            |
| 3306 | TCP      | MySQL          |
| 3389 | TCP      | RDP            |

---

## 🛠️ Tools & Suites

### 🔍 Reconnaissance
- `nmap`, `masscan` – Network mapping
- `subfinder`, `amass`, `assetfinder` – Subdomain enumeration
- `httpx`, `gau`, `waybackurls`, `hakrawler` – URL & endpoint discovery

### 🧪 Exploitation
- `Burp Suite`, `ZAP` – Proxy & web fuzzing
- `sqlmap` – SQL injection automation
- `xray`, `nuclei` – Template-based scanning
- `Metasploit`, `BeEF` – Exploits & browser hacking

### 🧬 Post-Exploitation
- `Mimikatz`, `CrackMapExec` – Credential dumping
- `BloodHound`, `SharpHound` – Active Directory recon
- `Empire`, `Sliver`, `Covenant` – C2 frameworks

---

## 📜 HTTP Methods & Status Codes

### Methods
- `GET`, `POST`, `PUT`, `DELETE`, `PATCH`, `OPTIONS`, `HEAD`

### Status Codes

| Code | Meaning                  |
|------|--------------------------|
| 200  | OK                       |
| 301  | Moved Permanently        |
| 302  | Found                    |
| 401  | Unauthorized             |
| 403  | Forbidden                |
| 404  | Not Found                |
| 500  | Internal Server Error    |
| 502  | Bad Gateway              |

---

# 🧠 MITRE ATT&CK Framework Cheat Sheet

> A compact reference to adversary Tactics, Techniques, and Procedures (TTPs) as outlined in the MITRE ATT&CK Framework.

## 📖 What is MITRE ATT&CK?

**MITRE ATT&CK** (Adversarial Tactics, Techniques, and Common Knowledge) is a globally accessible knowledge base of adversary behavior, based on real-world observations.

- Created by: [MITRE Corporation](https://mitre.org)
- URL: [https://attack.mitre.org](https://attack.mitre.org)

The matrix is divided into **14 Tactics** (adversary objectives), each containing **Techniques** and **Sub-techniques** (how the objective is achieved).

---

## 🧩 Tactics & Techniques Overview

| Tactic              | Description                             |
|---------------------|-----------------------------------------|
| Initial Access       | Entry point to the environment          |
| Execution            | Running adversary code                  |
| Persistence          | Maintaining access over time           |
| Privilege Escalation | Gaining higher-level permissions       |
| Defense Evasion      | Avoiding detection                     |
| Credential Access     | Stealing credentials                  |
| Discovery            | Understanding environment              |
| Lateral Movement     | Moving within the environment          |
| Collection           | Gathering target data                  |
| Command and Control  | Communicating with compromised systems |
| Exfiltration         | Stealing data                          |
| Impact               | Disrupting or destroying systems       |

---

## 🚪 Initial Access

| Technique                        | ID      | Description                            |
|----------------------------------|---------|----------------------------------------|
| Phishing                         | T1566   | Email-based delivery of malware        |
| Drive-by Compromise              | T1189   | Malicious site visits                  |
| Exploit Public-Facing App        | T1190   | Exploiting vulnerable web services     |
| Valid Accounts                   | T1078   | Use of legitimate credentials          |
| Supply Chain Compromise          | T1195   | Tampered software or hardware          |
| External Remote Services         | T1133   | RDP, VPN with stolen credentials       |

---

## 🧨 Execution

| Technique                        | ID      | Description                            |
|----------------------------------|---------|----------------------------------------|
| Command and Scripting Interpreter | T1059   | PowerShell, Bash, Python, etc.         |
| Scheduled Task/Job               | T1053   | Task Scheduler, cron jobs              |
| Exploitation for Execution       | T1203   | Exploiting vulnerabilities             |
| User Execution                   | T1204   | Tricking users to run malware          |

---

## 🔐 Persistence

| Technique                        | ID      | Description                            |
|----------------------------------|---------|----------------------------------------|
| Account Manipulation             | T1098   | Creating or modifying user accounts    |
| Registry Run Keys                | T1547.001 | Registry keys for startup execution   |
| Scheduled Task/Job               | T1053   | Persistence via task scheduling        |
| Boot or Logon Autostart Execution | T1547   | Starts on boot or logon                |

---

## 🔓 Privilege Escalation

| Technique                        | ID      | Description                            |
|----------------------------------|---------|----------------------------------------|
| Exploitation for Priv Esc        | T1068   | Exploiting OS vulnerabilities          |
| Process Injection                | T1055   | Code injection into processes          |
| Bypass User Account Control      | T1548.002 | UAC abuse                              |
| Token Impersonation/Theft       | T1134   | Using tokens of higher privilege       |

---

## 🕵️ Defense Evasion

| Technique                        | ID      | Description                            |
|----------------------------------|---------|----------------------------------------|
| Obfuscated Files or Information | T1027   | Encoding, packing, encryption          |
| Indicator Removal from Host     | T1070   | Deleting logs or artifacts             |
| Masquerading                    | T1036   | Renaming or spoofing legitimate files  |
| Signed Binary Proxy Execution   | T1218   | LOLBAS, trusted binaries               |

---

## 🔑 Credential Access

| Technique                        | ID      | Description                            |
|----------------------------------|---------|----------------------------------------|
| OS Credential Dumping           | T1003   | Dumping from LSASS, SAM, etc.          |
| Brute Force                     | T1110   | Password guessing                      |
| Keylogging                      | T1056.001 | Capturing user keystrokes             |
| Credential Stuffing             | T1110.004 | Reusing known credential sets         |

---

## 🧭 Discovery

| Technique                        | ID      | Description                            |
|----------------------------------|---------|----------------------------------------|
| System Information Discovery     | T1082   | OS, hostname, architecture             |
| File and Directory Discovery     | T1083   | Enumerate filesystem                   |
| Network Service Scanning         | T1046   | Port scanning                          |
| Process Discovery                | T1057   | List running processes                 |
| System Network Configuration Discovery | T1016 | IP, routing, DNS                      |

---

## 🔁 Lateral Movement

| Technique                        | ID      | Description                            |
|----------------------------------|---------|----------------------------------------|
| Remote Desktop Protocol (RDP)   | T1021.001 | RDP for movement                       |
| Windows Admin Shares            | T1077   | Using C$, ADMIN$                       |
| SSH                             | T1021.004 | SSH with credentials                   |
| Remote Services                 | T1021   | Move via exposed services              |
| Pass the Hash                   | T1550.002 | Authenticate without plaintext creds  |

---

## 📥 Collection

| Technique                        | ID      | Description                            |
|----------------------------------|---------|----------------------------------------|
| Clipboard Data                  | T1115   | Capturing copy-paste data              |
| Input Capture                   | T1056   | Keylogging, screen capture             |
| Audio Capture                   | T1123   | Microphone access                      |
| Screen Capture                  | T1113   | Taking screenshots                     |
| Automated Collection            | T1119   | Scripts/tools collecting files         |

---

## 🧬 Command and Control (C2)

| Technique                        | ID      | Description                            |
|----------------------------------|---------|----------------------------------------|
| Application Layer Protocol       | T1071   | HTTP/S, DNS for C2                     |
| Custom Command and Control Protocol | T1095 | Proprietary protocol for C2            |
| Web Service                      | T1102   | Use of social media, blogs             |
| Domain Fronting                  | T1090.004 | Bypass domain-based filtering         |
| Ingress Tool Transfer            | T1105   | Uploading tools from attacker server   |

---

## 🚨 Exfiltration

| Technique                        | ID      | Description                            |
|----------------------------------|---------|----------------------------------------|
| Exfiltration Over C2 Channel    | T1041   | Same channel as C2                     |
| Exfiltration Over Web Service   | T1567   | Dropbox, Google Drive                  |
| Exfiltration Over Alternative Protocol | T1048 | FTP, SCP                              |
| Archive Collected Data          | T1560   | ZIP or compress data before exfil      |

---

## 💥 Impact

| Technique                        | ID      | Description                            |
|----------------------------------|---------|----------------------------------------|
| Data Destruction                | T1485   | Wiping files or disks                  |
| Defacement                      | T1491   | Modifying websites or UI               |
| Data Encryption for Impact      | T1486   | Ransomware                             |
| Inhibit System Recovery         | T1490   | Deleting backups, shadow copies        |
| Service Stop                    | T1489   | Killing processes, disabling services  |

---

## 📎 Resources

- 🔗 [MITRE ATT&CK Website](https://attack.mitre.org/)
- 📘 [ATT&CK Navigator Tool](https://mitre-attack.github.io/attack-navigator/)
- 📂 [Atomic Red Team](https://github.com/redcanaryco/atomic-red-team)
- 🧠 [Sigma Rules](https://github.com/SigmaHQ/sigma) (ATT&CK-based detection)
- 📊 [Threat Reports via ATT&CK](https://attack.mitre.org/resources/attackcon/)

---




