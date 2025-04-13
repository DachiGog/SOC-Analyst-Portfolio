###📡 OSI Model

+--------+-----------------------------+----------------------------------+
| Layer  | Name                        | Example Protocols                |
+--------+-----------------------------+----------------------------------+
| 7      | Application                 | HTTP, FTP, DNS, SSH              |
| 6      | Presentation                | SSL/TLS, JPEG, ASCII             |
| 5      | Session                     | NetBIOS, PPTP                    |
| 4      | Transport                   | TCP, UDP                         |
| 3      | Network                     | IP, ICMP                         |
| 2      | Data Link                   | Ethernet, ARP                    |
| 1      | Physical                    | Fiber, Ethernet cables           |
+--------+-----------------------------+----------------------------------+

### 🔐 OWASP Top 10 (2023)

## Vulnerability	                 ## Description
1	Broken Access Control               Privilege escalation, IDOR
2	Cryptographic Failures	            Insecure transport or storage
3	Injection	                          SQL, NoSQL, OS command
4	Insecure Design	                    Poor architecture decisions
5	Security Misconfiguration	          Default creds, verbose errors
6	Vulnerable & Outdated Components	  Unpatched libraries or frameworks
7	Identification & Auth Failures	    Broken login or session control
8	Software & Data Integrity Failures	CI/CD pipeline compromise
9	Security Logging & Monitoring     	Missing detection/logging
10	SSRF	                            Targeting internal systems via request

### 🧩 Acronyms & Terminologies

Acronym	           Full Form	                            Description
APT	               Advanced Persistent Threat	            Long-term targeted attack
CVE	               Common Vulnerabilities & Exposures	    Public ID for known issues
CWE	               Common Weakness Enumeration	          Categories for software flaws
XSS	               Cross-Site Scripting	                  Injecting malicious JS
CSRF	             Cross-Site Request Forgery	            Forcing unwanted user actions
LFI	               Local File Inclusion	                  Load local server files
RFI	               Remote File Inclusion	                Load remote files in input
IDOR	             Insecure Direct Object Reference	      Access to unauthorized resources
SSRF	             Server-Side Request Forgery	          Server makes unwanted external requests
MITM	             Man In The Middle	                    Intercepting communications
JWT	               JSON Web Token	                        Auth token often used in APIs
ACL	               Access Control List	                  Permissions applied to resources

### 🧪 Common Attacks

Attack Type	              Description	                              Example Payload
SQL                       Injection	Manipulate SQL queries	        ' OR 1=1--
XSS                       (Reflected)	JS Injection in user input	  <script>alert(1)</script>
CSRF	                    Execute unwanted actions	                <img src="http://target/delete?user=1">
Command                   Injection	Execute system commands	        ; whoami
XXE	                      XML External Entity parsing	              <!ENTITY xxe SYSTEM "file:///etc/passwd">
Open                      Redirect	Redirect to untrusted domain	  ?redirect=https://evil.com

### 📦 Common Ports

Port	Protocol	Service
21	  TCP	      FTP
22	  TCP	      SSH
23	  TCP   	  Telnet
25	  TCP	      SMTP
53	  UDP/TCP	  DNS
80	  TCP	      HTTP
110	  TCP	      POP3
139	  TCP	      NetBIOS
143	  TCP	      IMAP
443	  TCP	      HTTPS
445	  TCP	      SMB
3306	TCP	      MySQL
3389	TCP	      RDP

###🛠️ Tools & Suites
#🔍 Recon
nmap, masscan, amass, subfinder, assetfinder

httpx, waybackurls, gau, hakrawler

#🧪 Exploitation
Burp Suite, ZAP, SQLmap, Xray, Nuclei

Metasploit, BeEF, Responder

#📦 Post-Exploitation
BloodHound, Mimikatz, CrackMapExec, SharpHound

Empire, Covenant, Sliver

###📜 HTTP Methods & Status Codes
Methods
GET, POST, PUT, DELETE, PATCH, OPTIONS, HEAD

Status Codes
Code	Meaning
200	OK
301	Moved Permanently
302	Found
401	Unauthorized
403	Forbidden
404	Not Found
500	Internal Server Error
502	Bad Gateway

### 🔁 Encoding & Obfuscation
Type	      Example
URL Encode	%3Cscript%3Ealert(1)%3C/script%3E
Base64	    PHNjcmlwdD5hbGVydCgxKTwvc2NyaXB0Pg==
Unicode	    \u003Cscript\u003Ealert(1)\u003C/script\u003E
