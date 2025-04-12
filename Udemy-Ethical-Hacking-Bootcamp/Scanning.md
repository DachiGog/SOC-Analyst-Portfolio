# 📡 Kali Linux Network Scanning - Nmap, Netdiscover & Evasion Techniques

## 🧠 What I Learned

This lab focused on using **Kali Linux** to perform network scanning against a **Metasploitable2 virtual machine**. 
I learned how to identify live hosts, discover open ports, determine the operating system, fingerprint service versions, and apply **evasion techniques** like using decoys and fragmented packets.

These are foundational skills for penetration testing and red team recon, as well as blue team defense and detection strategy.

---

## 📚 Topics Covered

- Network discovery with **Netdiscover**
- Active scanning using **Nmap**
- Identifying target **operating system and service versions**
- Using **Nmap evasion techniques** to bypass firewalls/IDS
- Metasploitable2 as a target for scanning and practice

---

## 🛠️ Tools Used

- **Kali Linux (VM)**
- **Metasploitable2 (VM target)**
- `nmap`
- `netdiscover`
- `ping`, `arp`, `ifconfig`, `ip`

---

🧪 Lab Setup
Host OS: Kali Linux (VirtualBox)
Target OS: Metasploitable2 (VM)

## 🔍 Scanning Workflow
### 1. Discover Target with Netdiscover

netdiscover -r 192.168.56.0/24
🟢 Output example:
192.168.56.101 - Metasploitable2
2. Basic Port Scan with Nmap
nmap 192.168.56.101
3. OS & Service Version Detection
nmap -sV -O 192.168.56.101
✅ Found:
Apache 2.2.8 (Ubuntu)
OpenSSH 4.7p1 Debian
OS: Linux 2.6.X
4. Full TCP Scan with Verbose Output
nmap -p- -vv 192.168.56.101
5. Stealth Scan (SYN Scan)
nmap -sS 192.168.56.101
🎭 Evasion Techniques
nmap -D RND:10 192.168.56.101
➡️ Sends decoy traffic from fake IPs to obscure true scanner
Fragmenting Packets
nmap -f 192.168.56.101
➡️ Splits probe into small IP fragments to evade firewalls
nmap --spoof-mac Cisco 192.168.56.101
