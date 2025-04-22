# 🐷 🐽 Snort - TryHackMe Room Writeup

## 🧠 What I Learned

NetworkMiner in a Nutshell

### Capabilities and Description
- Traffic sniffing  - *It can intercept the traffic, sniff it, and collect and log packets that pass through the network.*
- Parsing PCAP files  - *It can parse pcap files and show the content of the packets in detail.*
- Protocol analysis  - *It can identify the used protocols from the parsed pcap file.*
- OS fingerprinting  - *It can identify the used OS by reading the pcap file. This feature strongly relies on [Satori](https://github.com/xnih/satori/) and [p0f](https://lcamtuf.coredump.cx/p0f3/).*
- File Extraction  - *It can extract images, HTML files and emails from the parsed pcap file.*
- Credential grabbing  - *It can extract credentials from the parsed pcap file.*
- Clear text keyword parsing  - *It can extract cleartext keywords and strings from the parsed pcap file.*
  
---

## 📚 Topics Covered

- ### Intrusion Detection System (IDS):
  - IDS is a passive monitoring solution for detecting possible malicious activities/patterns, abnormal incidents, and policy violations. It is responsible for generating alerts for each suspicious event. 

- ### There are two main types of IDS systems;

  - Network Intrusion Detection System (NIDS) - NIDS monitors the traffic flow from various areas of the network. The aim is to investigate the traffic on the entire subnet. If a signature is identified, an alert is created.
  - Host-based Intrusion Detection System (HIDS) - HIDS monitors the traffic flow from a single endpoint device. The aim is to investigate the traffic on a particular device. If a signature is identified, an alert is created.

- ### ntrusion Prevention System (IPS):
  
  - IPS is an active protecting solution for preventing possible malicious activities/patterns, abnormal incidents, and policy violations. It is responsible for stopping/preventing/terminating the suspicious event as soon as the detection is performed.

  ### There are four main types of IPS systems;

  - Network Intrusion Prevention System (NIPS) - NIPS monitors the traffic flow from various areas of the network. The aim is to protect the traffic on the entire subnet. If a signature is identified, the connection is terminated.
  - Behaviour-based Intrusion Prevention System (Network Behaviour Analysis - NBA) - Behaviour-based systems monitor the traffic flow from various areas of the network. The aim is to protect the traffic on the entire subnet. If an anomaly is identified, the connection is terminated.

- ## Capabilities of Snort;

  - Live traffic analysis
  - Attack and probe detection
  - Packet logging
  - Protocol analysis
  - Real-time alerting
  - Modules & plugins
  - Pre-processors
  - Cross-platform support! (Linux & Windows)

- ##﻿ Snort in IDS/IPS Mode
  - IDS/IPS mode helps you manage the traffic according to user-defined rules.
- ## investigate PCAPs with Snort
  - Capabilities of Snort are not limited to sniffing, logging and detecting/preventing the threats. PCAP read/investigate mode helps you work with pcap files. Once you have a pcap file and process it with Snort, you will receive default traffic statistics with alerts depending on your ruleset.
    - *-r / --pcap-single=	Read a single pcap*
    - *--pcap-list=""	Read pcaps provided in command (space separated).*
    - *--pcap-show	Show pcap name on console during processing.*
- ## Snort Rules!
  - Understanding the Snort rule format is essential for any blue and purple teamer.  The primary structure of the snort rule is shown below;
  - ![Snort Rules](../../images/Snort/Snort-Rules.png)
  - IP Filtering	`alert icmp 192.168.1.56 any <> any any  (msg: "ICMP Packet From "; sid: 100001; rev:1;)`
  - Filter an IP range	`alert icmp 192.168.1.0/24 any <> any any  (msg: "ICMP Packet Found"; sid: 100001; rev:1;)`
  - Filter multiple IP ranges	`alert icmp [192.168.1.0/24, 10.1.1.0/24] any <> any any  (msg: "ICMP Packet Found"; sid: 100001; rev:1;)`
  - Exclude IP addresses/ranges  `alert icmp !192.168.1.0/24 any <> any any  (msg: "ICMP Packet Found"; sid: 100001; rev:1;)`
  - Port Filtering  `alert tcp any any <> any 21  (msg: "FTP Port 21 Command Activity Detected"; sid: 100001; rev:1;)`
  - Exclude a specific port  `alert tcp any any <> any !21  (msg: "Traffic Activity Without FTP Port 21 Command Channel"; sid: 100001; rev:1;)`
  - Filter a port range (Type 1)  `alert tcp any any <> any 1:1024   (msg: "TCP 1-1024 System Port Activity"; sid: 100001; rev:1;)`
  - Filter a port range (Type 2)  `alert tcp any any <> any :1024   (msg: "TCP 0-1024 System Port Activity"; sid: 100001; rev:1;)`
  - Filter a port range (Type 3)  `alert tcp any any <> any 1025: (msg: "TCP Non-System Port Activity"; sid: 100001; rev:1;)`
  - Filter a port range (Type 4)  `alert tcp any any <> any [21,23] (msg: "FTP and Telnet Port 21-23 Activity Detected"; sid: 100001; rev:1;)`
  - ID	Filtering the IP id field.  `alert tcp any any <> any any (msg: "ID TEST"; id:123456; sid: 100001; rev:1;)`
  - Flags	
      Filtering the TCP flags.

        F - FIN
        S - SYN
        R - RST
        P - PSH
        A - ACK
        U - URG
- ## Editing Rules
    - sudo gedit /etc/snort/snort.conf
    - sudo gedit /etc/snort/rules/local.rules
- ## Running snort pcap file with local rules
    - snort -c local.rules -A full -l . -r TEST.pcap
- - ## Reading snort
    - sudo snort -r Snort_LOG.pcap
---

## 🛠️ Tools Used

- Linux
- TryHackMe interactive lab environment
- Snort

---

## ✅ Status: Completed
