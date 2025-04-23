# 🛡️ Friday Overtime - Challange
---

## 🛠️ Tools Used
  - TryHackMe interactive lab environment
  - MITRE ATT&CK
  - Google
---
## 🔍 Scenario 1 Task - Anomalous DNS

An alert triggered: "Anomalous DNS Activity".

The case was assigned to you. Inspect the PCAP and retrieve the artefacts to confirm this alert is a true positive. 

- Investigate the dns-tunneling.pcap file. Investigate the dns.log file. What is the number of DNS records linked to the IPv6 address?
- First
- Second I used command `cat dns.log | zeek-cut qtype_name rcode | sort | uniq -c` to sort all uniq DNS and count them
- ![Zeek DNS Test Answer](../../images/Zeek/Zeek-dns-challange-1.png)
- ![Zeek DNS Test Answer](../../images/Zeek/Zeek-dns-challange-2.png)
- Investigate the conn.log file. What is the longest connection duration?
- To find the connection duration I used command `cat conn.log | zeek-cut duration | sort -k1n` 
- ![Zeek DNS Test Answer](../../images/Zeek/Zeek-dns-challange-3.png)
- Investigate the dns.log file. Filter all unique DNS queries. What is the number of unique domain queries?
- There are lots of ".cisco-update.com" DNS queries, I need to filter the main address and find out the rest of the queries that don't contain the ".cisco-update.com" pattern using command `cat dns.log | zeek-cut query |rev | cut -d '.' -f 1-2 | rev | sort | uniq`
- ![Zeek DNS Test Answer](../../images/Zeek/Zeek-dns-challange-4.png)
- There are a massive amount of DNS queries sent to the same domain. This is abnormal. Let's find out which hosts are involved in this activity. Investigate the conn.log file. What is the IP address of the source host?
- Used zeek-cut and sort to find the answer `cat conn.log | zeek-cut id.orig_h orig_bytes | sort -k1n`
- ![Zeek DNS Test Answer](../../images/Zeek/Zeek-dns-challange-5.png)

---
## ✅ Status: Completed

