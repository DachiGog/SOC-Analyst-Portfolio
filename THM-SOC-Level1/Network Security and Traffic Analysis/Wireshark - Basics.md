# WireShark - TryHackMe Room Writeup

## 🧠 What I Learned

Wireshark is an open-source, cross-platform network packet analyser tool capable of sniffing and investigating live traffic and inspecting packet captures (PCAP). It is commonly used as one of the best packet analysis tools. In this room, we will look at the basics of Wireshark and use it to perform fundamental packet analysis.
---

## 📚 most useful and commonly used Wireshark filters for SOC Analysts

### Basic IP Filters
  - Filter by IP address (source or destination) `ip.addr == 192.168.1.5`
  - Filter values	Filter source IP. `id.orig_h==192.168.121.40`
  - Filter by Destination IP only. `ip.dst == 192.168.1.5`
### Protocol Filters
  - Only DNS traffic. `dns`
  - Only HTTP traffic `http`
  - Only HTTPS traffic (SSL/TLS) `ssl || tls`
  - Only FTP traffic `ftp`
  - Only SSH traffic `tcp.port == 22`
  - Only RDP traffic `tcp.port == 3389`
  - Only DHCP traffic `bootp`
  - Only ICMP (Ping) traffic `icmp`
### Port and Service Filters
  - Traffic to or from a specific port `tcp.port == 443`
  - Filter TCP traffic only `tcp`
  - Filter UDP traffic only `udp`
### Security Focused Filters
  - Filter suspicious DNS queries (e.g., long domains) `dns.qry.name contains "."`
  - Filter for failed TLS handshakes (potential scanning or misconfiguration) `tls.handshake.type == 1 and ssl.record.version == 0x0301`
  - Show only retransmissions (could indicate issues or attacks) `tcp.analysis.retransmission`
  - Show duplicate ACKs (could be attack or network issue) `tcp.analysis.duplicate_ack`
  - Filter for HTTP requests (good for catching C2 callbacks or exfil attempts) `http.request`
### File Transfers & Exfiltration Filters
  - Detect file uploads over HTTP `http.request.method == "POST"`
  - Detect large file transfers (over TCP) `frame.len > 1000`
### Other Highly Useful Filters
  - Show only TCP SYN packets (possible scanning) `tcp.flags.syn == 1 and tcp.flags.ack == 0`
  - Show TCP reset packets (RST) (could signal scans or failed sessions) `tcp.flags.reset == 1`
  - Follow a specific TCP stream (replace 1234 with the stream index) `tcp.stream eq 1234`
  - Find packets with errors `tcp.analysis.flags`
  - Traffic within a subnet `ip.addr == 10.0.0.0/8`
### Pro Tip:
  - You can combine filters with and, or, not. `(ip.addr == 192.168.1.5) and (tcp.port == 443)`
## Deep & Complex Wireshark Filters for SOC Analysts
### Advanced IP, Port, and Protocol Filtering
  - Exclude Noise IPs (like known internal subnets): `ip.addr != 10.0.0.0/8 and ip.addr != 192.168.0.0/16 and ip.addr != 172.16.0.0/12
`
  - Detect Uncommon Ports (potential C2): `tcp.port != 80 and tcp.port != 443 and tcp.port != 22 and tcp.port != 3389`
  - Traffic between two specific hosts: `(ip.src == 192.168.1.5 and ip.dst == 10.10.10.5) or (ip.src == 10.10.10.5 and ip.dst == 192.168.1.5)`
### DNS Hunting (Suspicious Lookups)
- Suspicious domain patterns (long, random-looking): `dns.qry.name matches "[A-Za-z0-9]{20,}\."`
- Non-standard DNS ports (could be DNS tunneling): `udp.port != 53 and dns`
- Multiple DNS queries in a short time (possible DGA): `frame[0:0] and dns and frame.time_delta < 0.1`
- Queries for TXT records (potential DNS tunneling): `dns.qry.type == 16`
### SSL/TLS Deeper Analysis
- Weak SSL/TLS Cipher Suites: `ssl.handshake.ciphersuite in {0x0004, 0x0005, 0x000a}`
- SSL Certificate Anomalies (self-signed, invalid): `ssl.handshake.extensions_server_name and ssl.handshake.certificates`
- SSL/TLS Sessions without SNI (suspicious in modern traffic): `tls.handshake.extensions_server_name == ""`
- Self-signed SSL Certificates (might be malware C2): `ssl.handshake.certificate.issuer == ssl.handshake.certificate.subject`
### Suspicious TCP Patterns
  - TCP connections without 3-way handshake (half-open SYN floods or stealth): `tcp.flags.syn == 1 and tcp.flags.ack == 0`
  - Multiple RSTs (scanning, failed connections): `tcp.flags.reset == 1`
  - High Delta Times between TCP packets (might signal C2 idle sessions): `tcp.analysis.flags and frame.time_delta > 5`
  - ACK Storm Detection (could signal exfil or attack): `tcp.flags.ack == 1 and tcp.len == 0`
### Payload & File Exfiltration Detection
  - HTTP with large POST bodies (exfiltration): `http.request.method == "POST" and http.content_length > 100000`
  - Suspicious SMB Traffic (file transfer in internal lateral movement): `smb2 and smb2.cmd == 5`
  - FTP Transfers of Files: `ftp.request.command == "STOR"`
### Behavior and Timing Based Filters
  - Rapid sessions from one IP (brute force or botnet activity): `ip.src == x.x.x.x and frame.time_delta < 0.05`
  - Small, repetitive packets (C2 beaconing or scans): `frame.len < 100 and frame.time_delta > 30`
  - Beaconing Behavior over HTTP: `http.request and frame.time_delta > 10 and frame.time_delta < 60`
### Miscellaneous Advanced Filters
  - Malformed Packets (attempted evasion or fuzzing attacks): `frame.protocols contains "malformed"`
  - Packets with Bad Checksums (possible spoofing): `ip.checksum_bad == 1`
  - Traffic without Host Header in HTTP (potential malware): `http.host == ""`
  - Empty User-Agent Strings (suspicious automated tools): `http.user_agent == ""`
### PRO ADVANCED COMBINATION EXAMPLES
  - Look for large HTTP POSTs and suspicious DNS at the same time (data exfiltration + C2 setup): `(http.request.method == "POST" and http.content_length > 50000) or (dns.qry.type == 16)`
  - Detect Potential Command-and-Control over SSL/TLS (no SNI + uncommon ports): `(tls.handshake.extensions_server_name == "") and (tcp.port != 443)`
### Bonus: Useful Display Filter Shortcuts
  - Highlight a suspicious stream: `tcp.stream eq 5`
  - Focus on one conversation (IP pair + port): `ip.addr==x.x.x.x and tcp.port==yyyy`

---

## 🛠️ Tools Used

- Linux
- TryHackMe interactive lab environment
- Wireshark

---

## ✅ Status: Completed
