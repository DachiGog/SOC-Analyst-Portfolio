# 🛡️ Sysmon Setup Guide - Windows Event Monitoring for Threat Detection

## 🧠 What I Learned

In this setup, I deployed **Sysmon (System Monitor)** on a Windows system to collect detailed event logs such as process creation, network connections, and file changes. I learned how to install and configure Sysmon using a community config and verified the logs in **Event Viewer** for use in threat detection and log analysis.

This is an essential skill for blue teamers and SOC analysts working with Windows endpoints.

---

## 📚 Topics Covered

- Downloading and installing Sysmon
- Using a well-structured configuration file (SwiftOnSecurity’s config)
- Logging key telemetry: Process creation, command-line args, network activity
- Viewing Sysmon logs in **Event Viewer**
- Verifying proper installation and event generation

---

## 🛠️ Tools Used

- [Sysmon from Sysinternals](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)
- [SwiftOnSecurity Sysmon Config](https://github.com/SwiftOnSecurity/sysmon-config)
- Windows Event Viewer
- PowerShell / CMD

---

## 🔧 Installation Steps

### 1. 📥 Download Sysmon

From the official Microsoft site:  
[https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)

Extract the zip (e.g., `Sysmon64.exe`, `Sysmon.exe`)

---

### 2. 📄 Get a Config File

I used SwiftOnSecurity’s config:

git clone https://github.com/SwiftOnSecurity/sysmon-config.git
cd sysmon-config

### 3. 🧪 Install Sysmon with Config

Sysmon64.exe -accepteula -i sysmonconfig-export.xml

### ✔️ You should see:
Sysmon successfully installed.

### 4. 🔍 Verify in Event Viewer
Event Viewer → Applications and Services Logs → Microsoft → Windows → Sysmon → Operational

Check for event IDs like:
1 - Process creation
3 - Network connection
11 - FileCreate

### 🧰 Useful Commands
Check status:
  - sc query sysmon
Uninstall:
  - Sysmon64.exe -u
Update config:
  - Sysmon64.exe -c newconfig.xml

### 📌 Use Cases
Track process chains in real time

Identify lateral movement or suspicious binaries

Build Sigma rules or forward logs to SIEM

Essential for threat hunting and correlation
