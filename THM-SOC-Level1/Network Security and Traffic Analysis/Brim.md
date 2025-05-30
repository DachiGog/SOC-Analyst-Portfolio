# Brim - TryHackMe Room Writeup

## 🧠 What I Learned

  Brim is an open-source desktop application that processes pcap files and logs files, with a primary focus on providing search and analytics. It uses the Zeek log processing format. It also supports Zeek signatures and Suricata Rules for detection.
---

## 📚 Topics Covered

- ### Custom Queries and Use Cases:

  - Basic search Find logs containing an IP address or any value. `10.0.0.1`
  - Logical operators Find logs contain three digits of an IP AND NTP keyword. `192 and NTP`
  - Filter values	Filter source IP. `id.orig_h==192.168.121.40`
  - List specific log file contents List the contents of the conn log file. `_path=="conn"`
  - Count field values 	Count the number of the available log files. `count () by _path`
  - Sort findings Count the number of the available log files and sort recursively. `count () by _path | sort -r`
  - Cut specific field from a log file *Cut the source IP, destination port and destination IP addresses from the conn log file.* `_path=="conn" | cut id.orig_h, id.resp_p, id.resp_h`
  - List unique values *Show the unique network connections. * `_path=="conn" | cut id.orig_h, id.resp_p, id.resp_h | sort | uniq`
 
  - Communicated Hosts `_path=="conn" | cut id.orig_h, id.resp_h | sort | uniq`
  - Frequently Communicated Hosts `_path=="conn" | cut id.orig_h, id.resp_h | sort | uniq -c | sort -r`
  - Most Active Ports `path=="conn" | cut id.resp_p, service | sort | uniq -c | sort -r count` and `_path=="conn" | cut id.orig_h, id.resp_h, id.resp_p, service | sort id.resp_p | uniq -c | sort -r`
  - Long Connections `_path=="conn" | cut id.orig_h, id.resp_p, id.resp_h, duration | sort -r duration`
  - Transferred Data `_path=="conn" | put total_bytes := orig_bytes + resp_bytes | sort -r total_bytes | cut uid, id, orig_bytes, resp_bytes, total_bytes`
  - DNS and HTTP Queries `_path=="dns" | count () by query | sort -r` and `_path=="http" | count () by uri | sort -r`
  - Suspicious Hostnames `_path=="dhcp" | cut host_name, domain`
  - Suspicious IP Addresses `_path=="conn" | put classnet := network_of(id.resp_h) | cut classnet | count() by classnet | sort -r`
  - Detect Files `filename!=null`
  - Known Patterns `event_type=="alert" or _path=="notice" or _path=="signatures"`

- ## Exercise: Threat Hunting with Brim | Malware C2 Detection
  
  It is just another malware campaign spread with CobaltStrike. We know an employee clicks on a link, downloads a file, and then network speed issues and anomalous traffic activity arises

  - First I Reviewed the frequently communicated hosts before starting to investigate individual logs `cut id.orig_h, id.resp_p, id.resp_h | sort  | uniq -c | sort -r count`
  - ![](../../images/Brim/Brim-challange-1-1.png)
  - After first glance IPs 10.22.xx" and "104.168.xx draw attention  `_path=="conn" | cut id.resp_p, service | sort | uniq -c | sort -r count`
  - ![](../../images/Brim/Brim-challange-1-2.png)
  - Nothing extremely odd in port numbers, but there is a massive DNS record available. Let's have a closer look. `_path=="dns" | count() by query | sort -r`
  - ![](../../images/Brim/Brim-challange-1-3.png)
  - ![](../../images/Brim/Brim-challange-1-4.png)
  - We detect a file download request from the IP address we assumed as malicious. Let's validate this idea with VirusTotal and validate our hypothesis.
  - ![](../../images/Brim/Brim-challange-1-5.png)
  - ![](../../images/Brim/Brim-challange-1-6.png)
  - Now let's conclude our hunt by gathering with Suricata logs.
  - ![](../../images/Brim/Brim-challange-1-7.png)
---

## 🛠️ Tools Used

- Linux
- TryHackMe interactive lab environment
- Brim

---

## ✅ Status: Completed
