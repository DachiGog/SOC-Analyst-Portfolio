# Splunk - Overview and Log Management Fundamentals

## 📘 Overview

**Splunk** is a powerful platform for searching, analyzing, and visualizing machine-generated data in real-time. It is widely used in **Security Operations Centers (SOC)**, **DevOps**, and **IT operations** for log management, event correlation, alerting, and dashboarding.

Splunk ingests data from a variety of sources—such as system logs, application logs, network traffic, and cloud services—and enables actionable insights through powerful querying and visualization capabilities.

---

## 🧱 Splunk Components and How They Work

Splunk operates on a **distributed architecture**, with multiple components working together:

### 1. **Forwarder**
- **Universal Forwarder (UF)**: Lightweight agent installed on source machines to send logs to indexers.
- **Heavy Forwarder (HF)**: Parses data before forwarding, useful for filtering or routing logs.

### 2. **Indexer**
- Core component that **parses**, **indexes**, and **stores** incoming data.
- Creates time-series events and stores them for efficient searching.

### 3. **Search Head**
- User interface for running searches, creating dashboards, and managing alerts.
- Supports SPL (Search Processing Language) for querying indexed data.

### 4. **Deployment Server**
- Manages and updates configuration of multiple forwarders from a central location.

### 5. **License Master & Cluster Master**
- License Master: Manages Splunk license usage
- Cluster Master: Manages indexer clusters in distributed environments

Data Flow: Forwarder ➜ Indexer ➜ Search Head

---

## 📥 Different Ways to Ingest Logs into Splunk

Splunk supports various data ingestion methods, making it highly adaptable for different environments.

### 🔹 1. File and Directory Monitoring
# Inputs.conf example for monitoring /var/log
[monitor:///var/log]
disabled = false
index = syslog
sourcetype = linux_logs

🔹 2. Syslog (UDP/TCP)
Splunk can receive logs directly from network devices like firewalls or routers.
`[udp://514]
sourcetype = syslog
index = network`

🔹 3. APIs and HTTP Event Collector (HEC)
Send logs over HTTP(S) using tokens.
`POST https://splunk.example.com:8088/services/collector/event
Header: Authorization: Splunk <HEC_Token>`

🔹 4. Cloud Integrations
AWS: CloudTrail, CloudWatch, S3

Azure, GCP: via Splunk add-ons or HEC

🔹 5. Add-ons & Modular Inputs
Use Splunkbase apps to ingest specialized data sources like Windows Event Logs, Palo Alto logs, or Zeek logs.

🧹 Normalization of Logs
Normalization ensures that logs from different sources are standardized for efficient correlation and analysis.

Why Normalize?
Different systems use different log formats (e.g., Apache vs. Windows)

Enables consistent field naming (e.g., src_ip, dest_ip, user)

Facilitates threat detection and compliance reporting

Tools for Normalization
1. Field Extraction
Use props.conf and transforms.conf to extract fields using regex or Delimiters.
`# Example field extraction in props.conf
[apache_logs]
TRANSFORMS-extract = extract_apache_fields`

2. Data Models (Common Information Model - CIM)
Maps raw logs into standardized schemas

Required for apps like Splunk Enterprise Security (ES)
`Example: Map "source_ip" from firewall logs to CIM field `src`

3. Event Types and Tags
Event types categorize logs for use in alerts or dashboards

Tags label data for better classification

📈 Example: Search Query (SPL)
`index=windows sourcetype=WinEventLog:Security EventCode=4625
| stats count by Account_Name, host, src_ip
| sort -count`
🔍 This query finds failed login attempts by user and source IP.

🧠 Summary
Topic	Summary
Components	    Forwarders send data to Indexers, which are queried via Search Heads
Ingestion       Methods	Files, Syslog, API, Cloud services, and Add-ons
Normalization	  Ensures consistent field names using field extraction and CIM
Use Cases	      Threat hunting, compliance, IT operations, and real-time monitoring
