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
  <pre> ```event zeek_init()
    {
     print ("Started Zeek!");
    }
event zeek_done()
    {
    print ("Stopped Zeek!");
    }``` </pre>

# zeek_init: Do actions once Zeek starts its process.
# zeek_done: Do activities once Zeek finishes its process.
# print: Prompt a message on the terminal.
---

## 🛠️ Tools Used

- Linux
- TryHackMe interactive lab environment
- Zeek

---

## ✅ Status: Completed
