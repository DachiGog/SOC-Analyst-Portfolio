# Sysmon & Sysinternals - Monitoring and Threat Hunting

## Overview

This write-up explores **Sysmon (System Monitor)** and other essential tools from the **Sysinternals Suite** by Microsoft. These tools are widely used by security analysts, incident responders, and system administrators for system monitoring, threat detection, and forensic investigations.

- **Category**: Windows Monitoring & Incident Response
- **Tools Covered**: Sysmon, Process Explorer, Autoruns, TCPView, PsExec, and more
- **Skill Level**: Intermediate
- **Use Case**: Threat detection, malware analysis, and system auditing

---

## 🔧 What is Sysinternals?

**Sysinternals** is a collection of Windows utilities designed to help manage, troubleshoot, and diagnose Windows systems. Notable tools include:

- **Process Explorer** – Detailed information on running processes
- **Autoruns** – View of programs that run at startup
- **TCPView** – Network connections in real time
- **PsExec** – Remote execution of processes

---

## 🔍 What is Sysmon?

**Sysmon** is a Windows system service and device driver that logs system activity to the Windows Event Log. It provides detailed information on:

- Process creation and termination
- Network connections
- File creation timestamps
- Registry modifications
- WMI events and more

Sysmon enhances native Windows event logging by providing richer, security-relevant data.

---

## 🛠️ Installing Sysmon

```bash
# Download Sysinternals from:
# https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon

# Example install command:
sysmon.exe -accepteula -i sysmonconfig.xml
```
You can install Sysmon with a custom configuration to specify which events to monitor. A popular config is provided by SwiftOnSecurity:

https://github.com/SwiftOnSecurity/sysmon-config

🧪 Example Use Cases
🧷 1. Detecting Suspicious Process Injection
`Event ID: 8 (CreateRemoteThread)
Details: Process A (legitimate) injected code into Process B (e.g., explorer.exe)`
This is often used by malware to stay hidden. Sysmon logs can reveal this under Event ID 8.

🌐 2. Monitoring Network Connections
`Event ID: 3 (Network Connection)
Image: C:\Users\victim\AppData\Roaming\malware.exe
Destination IP: 192.168.56.100:4444`
This indicates the malware is connecting to a C2 server, which may be missed by native logs.

🛠️ 3. Startup Persistence with Autoruns
Using autoruns.exe, we can identify unexpected programs set to auto-run on startup:
`HKCU\Software\Microsoft\Windows\CurrentVersion\Run
suspicious.exe  ->  C:\Users\victim\AppData\malicious.exe`

 📊 4. Real-Time Process Analysis with Process Explorer
Using procexp.exe, view the parent-child relationship of suspicious processes:
`cmd.exe > powershell.exe > rundll32.exe`
This can indicate script-based attacks or Living Off the Land Binaries (LOLBins).

🔁 5. Remote Code Execution with PsExec
Sysinternals’ PsExec allows testing or detecting lateral movement techniques:
`psexec.exe \\target -u admin -p password cmd.exe`
Sysmon logs this under Event ID 1 (process creation) and includes remote execution details.

📂 Event ID Summary (Sysmon)
Event ID	Description
1	Process creation
3	Network connection
7	Image loaded (DLLs)
8	CreateRemoteThread detected
11	File created
13	Registry value set
22	DNS query

🔐 Use in Threat Hunting
Sysmon and Sysinternals together allow defenders to:
Detect abnormal process behavior
Monitor lateral movement techniques
Track persistence mechanisms
Hunt for malware and rootkits
Correlate events with MITRE ATT&CK techniques

