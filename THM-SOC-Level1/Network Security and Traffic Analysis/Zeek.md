# Zeek - TryHackMe Room Writeup

## 🧠 What I Learned

"Zeek (formerly Bro) is the world's leading platform for network security monitoring. Flexible, open-source, and powered by defenders." "Zeek is a passive, open-source network traffic analyser. Many operators use Zeek as a network security monitor (NSM) to support suspicious or malicious activity investigations. Zeek also supports a wide range of traffic analysis tasks beyond the security domain, including performance measurement and troubleshooting."

[Zeek script Learning Platform](https://try.bro.org/#/?example=hello)
---

## 📚 Topics Covered

- ### Zeek Architecture:
  - Zeek has two primary layers; "Event Engine" and "Policy Script Interpreter". The Event Engine layer is where the packets are processed; it is called the event core and is responsible for describing the event without focusing on event details. It is where the packages are divided into parts such as source and destination addresses, protocol identification, session analysis and file extraction.
  - The Policy Script Interpreter layer is where the semantic analysis is conducted. It is responsible for describing the event correlations by using Zeek scripts.

- ### Zeek Frameworks:

  - Zeek has several frameworks to provide extended functionality in the scripting layer. These frameworks enhance Zeek's flexibility and compatibility with other network components. Each framework focuses on the specific use case and easily runs with Zeek installation.
  - For instance, we will be using the "Logging Framework" for all cases. Having ide on each framework's functionality can help users quickly identify an event of interest.
  - 
- ### Zeek Outputs:
  
  - As mentioned before, Zeek provides 50+ log files under seven different categories, which are helpful in various areas such as traffic monitoring, intrusion detection, threat hunting and web analytics
  - Once you run Zeek, it will automatically start investigating the traffic or the given pcap file and generate logs automatically. Once you process a pcap with Zeek, it will create the logs in the working directory.
  - If you run the Zeek as a service, your logs will be located in the default log path. The default log path is: /opt/zeek/logs/
  - 
  ### Working with Zeek:

  -Here we can manage the Zeek service and view the status of the service. Primary management of the Zeek service is done with three commands; "status", "start", and "stop".
  -![]()
  - zeekctl status
  - zeekctl start 
  - zeekctl stop

    Parameters and Description
  - -r	 Reading option, read/process a pcap file.
  - -C	 Ignoring checksum errors.
  - -v	 Version information.
  - zeekctl	ZeekControl module.
    
- ## Zeek Logs:

  - Network - Network protocol logs. *conn.log, dce_rpc.log, dhcp.log, dnp3.log, dns.log, ftp.log, http.log, irc.log,
                        kerberos.log, modbus.log, modbus_register_change.log, mysql.log, ntlm.log, ntp.log,
                        radius.log, rdp.log, rfb.log, sip.log, smb_cmd.log, smb_files.log, smb_mapping.log,
                        smtp.log, snmp.log, socks.log, ssh.log, ssl.log, syslog.log, tunnel.log.*
  - Files File - analysis result logs. *files.log, ocsp.log, pe.log, x509.log.*
  - NetControl - Network control and flow logs. *netcontrol.log, netcontrol_drop.log, netcontrol_shunt.log, netcontrol_catch_release.log, openflow.log.*
  - Detection - Detection and possible indicator logs. *intel.log, notice.log, notice_alarm.log, signatures.log, traceroute.log.*
  - Network Observations - Network flow logs. *known_certs.log, known_hosts.log, known_modbus.log, known_services.log, software.log.*
  - Miscellaneous - Additional logs cover external alerts, inputs and failures. *barnyard2.log, dpd.log, unified2.log, unknown_protocols.log, weird.log, weird_stats.log.*
  - Zeek Diagnostic - Zeek diagnostic logs cover system messages, actions and some statistics. *broker.log, capture_loss.log, cluster.log, config.log, loaded_scripts.log, packet_filter.log, print.log, prof.log, reporter.log, stats.log, stderr.log, stdout.log.*

[Zeek's official documentation](https://docs.zeek.org/en/current/script-reference/log-files.html)
[https://corelight.com/products/zeek-data/](https://corelight.com/products/zeek-data/)

Zeek-cut	Cut specific columns from zeek logs.

- ##﻿ CLI Kung-Fu Recall: Processing Zeek Logs
  - `cheetsheets/Linux-Basic-Command-Lines.md`

- ## Zeek Signatures
  - Condition Field Available Filters
  - Header
           - src-ip: Source IP.
           - dst-ip: Destination IP.
           - src-port: Source port.
           - dst-port: Destination port.
           - ip-proto: Target protocol. Supported protocols; TCP, UDP, ICMP, ICMP6, IP, IP6     
  - Content
            - payload: Packet payload.
            - http-request: Decoded HTTP requests.
            - http-request-header: Client-side HTTP headers.
            - http-request-body: Client-side HTTP request bodys.
            - http-reply-header: Server-side HTTP headers.
            - http-reply-body: Server-side HTTP request bodys.
            - ftp: Command line input of FTP sessions.
  - Context
            - same-ip: Filtering the source and destination addresses for duplication.     
  - Action
            - event: Signature match message.
  - Comparison Operators
            - ==, !=, <, <=, >, >=
  - NOTE!
            - Filters accept string, numeric and regex values.    
- ## Zeek filtering Example
  - `cat signatures.log | zeek-cut src_addr dst_addr event_msg sub_msg | sort -r| uniq`   

- ## Zeek Scripts
  - Zeek has base scripts installed by default, and these are not intended to be modified.
        -  "/opt/zeek/share/zeek/base".
  - User-generated or modified scripts should be located in a specific path.
        - "/opt/zeek/share/zeek/site".
  - Policy scripts are located in a specific path.
        -  "/opt/zeek/share/zeek/policy".
  -  "/opt/zeek/share/zeek/policy".
        - "/opt/zeek/share/zeek/site/local.zeek".  

- ## Scripts 101 | Write Basic Scripts
         event zeek_init()
            {
             print ("Started Zeek!");
            }
         event zeek_done()
            {
             print ("Stopped Zeek!");
            }

      # zeek_init: Do actions once Zeek starts its process.
      # zeek_done: Do activities once Zeek finishes its process.
      # print: Prompt a message on the terminal. </pre>

      ubuntu@ubuntu$ zeek -C -r sample.pcap 101.zeek 
      Started Zeek!
      Stopped Zeek!
  - ## Script Examples
            zeek -C -r sample.pcap 103.zeek
            cat conn.log | zeek-cut uid | sort | uniq | wc -l

        zeek -C -r ftp.pcap 201.zeek -s ftp-admin.sig | wc -l
        cat signatures.log | zeek-cut sub_msg | grep "USER administrator" | wc -l

- ## Zeek Scripts | Frameworks
  - File Framework | Hashes
    - You can easily see the usage of frameworks in scripts by calling a specific framework as `load @ $PATH/base/frameworks/framework-name `
            <pre/> ubuntu@ubuntu$ cat hash-demo.zeek 
                  # Enable MD5, SHA1 and SHA256 hashing for all files.
                  @load /opt/zeek/share/zeek/policy/frameworks/files/hash-all-files.zeek </pre>
      - Grab File Hashes
<pre/> ubuntu@ubuntu$ zeek -C -r case1.pcap hash-demo.zeek
        ubuntu@ubuntu$ zeek -C -r case1.pcap /opt/zeek/share/zeek/policy/frameworks/files/hash-all-files.zeek 

        ubuntu@ubuntu$ cat files.log | zeek-cut md5 sha1 sha256
        cd5a4d3fdd5bffc16bf959ef75cf37bc	33bf88d5b82df3723d5863c7d23445e345828904	6137f8db2192e638e13610f75e73b9247c05f4706f0afd1fdb132d86de6b4012
        b5243ec1df7d1d5304189e7db2744128	a66bd2557016377dfb95a87c21180e52b23d2e4e	f808229aa516ba134889f81cd699b8d246d46d796b55e13bee87435889a054fb
        cc28e40b46237ab6d5282199ef78c464	0d5c820002cf93384016bd4a2628dcc5101211f4	749e161661290e8a2d190b1a66469744127bc25bf46e5d0c6f2e835f4b92db18 </pre>

      -  Extract files
     <pre/> ubuntu@ubuntu$ zeek -C -r case1.pcap /opt/zeek/share/zeek/policy/frameworks/files/extract-all-files.zeek

            ubuntu@ubuntu$ ls
            101.zeek  102.zeek  103.zeek  case1.pcap  clear-logs.sh  conn.log  dhcp.log  dns.log  extract_files  files.log  ftp.pcap  http.log  packet_filter.log  pe.log  </pre>

      -  Investigate Files
       <pre/>  ubuntu@ubuntu$ ls extract_files | nl
     1	extract-1561667874.743959-HTTP-Fpgan59p6uvNzLFja
     2	extract-1561667889.703239-HTTP-FB5o2Hcauv7vpQ8y3
     3	extract-1561667899.060086-HTTP-FOghls3WpIjKpvXaEl

          ubuntu@ubuntu$ cd extract_files

          ubuntu@ubuntu$ file *| nl
       1	extract-1561667874.743959-HTTP-Fpgan59p6uvNzLFja:  ASCII text, with no line terminators
       2	extract-1561667889.703239-HTTP-FB5o2Hcauv7vpQ8y3:  Composite Document File V2 Document, Little Endian, Os: Windows, Version 6.3, Code page: 1252, Template: Normal.dotm, Last Saved By: Administrator, Revision             Number: 2, Name of Creating Application: Microsoft Office Word, Create Time/Date: Thu Jun 27 18:24:00 2019, Last Saved Time/Date: Thu Jun 27 18:24:00 2019, Number of Pages: 1, Number of Words: 0, Number of Characters: 1, Security: 0 </pre>
---

## 🛠️ Tools Used

- Linux
- TryHackMe interactive lab environment
- Zeek

---

## ✅ Status: Completed
