# 🐱‍💻 Kali Linux Essentials - File Ops, Networking & Sudo

## 🧠 What I Learned

This session focused on getting comfortable with **Kali Linux**, especially how to navigate the file system, manage directories and files, run basic network diagnostics, and understand how `sudo` gives privileged access.

These are core Linux skills for both offensive and defensive security work, especially in a SOC or red team setting.

---

## 📚 Topics Covered

- Linux file system structure
- Creating, moving, and deleting files and folders
- File permissions and execution rights
- Basic network commands: `ip`, `ifconfig`, `ping`, `netstat`, `ss`
- Understanding and using `sudo` for privileged tasks
- Editing files with `nano` and `vim`

---

## 🛠️ Commands Practiced

🧰 Tools Used
Kali Linux terminal
nano, vim (file editing)
ls, tree (directory visualization)
ping, netstat, ip (network diagnostics)

🔑 Using sudo
bash
Copiar
Editar
sudo apt update
sudo cat /etc/shadow
sudo nano /etc/hosts

🌐 Network Basics
bash
Copiar
Editar
ip a
ifconfig
ping 1.1.1.1
netstat -tuln
ss -tulwn

### 📁 File & Directory Operations
```bash
mkdir recon
touch notes.txt
mv notes.txt recon/
rm -rf test_folder/
chmod +x script.sh
