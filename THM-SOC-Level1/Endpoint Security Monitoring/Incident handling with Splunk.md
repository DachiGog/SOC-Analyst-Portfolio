## 1. Reconnaissance
Goal: Identify if the attacker performed any scanning or enumeration prior to the attack.

Splunk Queries:
``index=network_logs OR index=firewall_logs
(sourcetype=nmap OR useragent=*scanner* OR uri_path=*robots.txt*)``
  Look for IPs accessing .git, .env, robots.txt, or scanning various endpoints.
  Check unusual traffic spikes or repeated failed requests.

## 2. Weaponization
  Goal: Determine if any malicious payloads were prepared.
  This step might not be directly observable in Splunk logs unless the payload was hosted internally or uploaded.
`index=web_logs uri_path IN ("/upload", "/admin", "/filemanager") OR http_method=POST`

Splunk Hint:
  - Look for suspicious file uploads:
  - `index=web_logs uri_path IN ("/upload", "/admin", "/filemanager") OR http_method=POST`

## 3. Delivery
  Goal: Identify how the payload or attack was delivered (e.g., phishing, exploit, malicious file).

Splunk Queries:
`index=web_logs OR index=proxy_logs
(uri_path=*upload* OR uri=*php?cmd=* OR url=*base64*)`
  Look for encoded payloads or suspicious URLs with command injections or file uploads.

## 4. Exploitation
  Goal: Confirm if a vulnerability was exploited (e.g., RCE, LFI, SQLi).

Splunk Queries:
`index=web_logs
(uri_path="*.php" AND (uri_query="*cmd=" OR uri_query="*exec=" OR uri_query="*system="))`
  Check for unusual POST requests or parameters.
  Look for exploitation tools or payloads (e.g., curl, wget, eval, base64).

## 5. Installation
  Goal: Determine if the attacker installed a web shell or malicious code.

Splunk Queries:
`index=web_logs uri_path="*shell*" OR uri_path="*cmd.php" OR file="*.php"`
  Search for new or unauthorized scripts on the server.
  Cross-check with file integrity monitoring alerts.

## 6. Command and Control (C2)
  Goal: Identify if there was outbound traffic from the compromised server.

Splunk Queries:
`index=network_logs dest_ip!=internal_ip_range
(http_user_agent="curl" OR http_user_agent="wget" OR uri_query="*cmd=")`
  Look for traffic to suspicious IPs or domains.
  Detect data exfiltration attempts or remote control behavior.

## 7. Actions on Objectives
  Goal: Confirm the defacement activity.

Splunk Queries:
`index=web_logs uri_path="/index.html" OR uri_path="/home" OR uri_path="/main"
| stats latest(_time) by uri_path, http_status, http_method, src_ip`
  Use file integrity monitoring logs to find changes to index.html.
  Identify who modified it and when.

## Bonus: Triage & Response
  Tag all relevant IPs and artifacts as IOCs.
  Isolate the compromised web server.
  Create a timeline of the intrusion.
  Check for lateral movement in related logs (internal network access, RDP, etc.).
