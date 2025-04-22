# 🐧 Linux Command Cheatsheet

Your go-to reference for essential Linux commands — categorized for quick lookup!

---

## 📦 Basic Commands

| Command            | Description                          |
|--------------------|--------------------------------------|
| `pwd`              | Show current directory path          |
| `ls`               | List directory contents              |
| `cd`               | Change directory                     |
| `mkdir <dir>`      | Create a new directory               |
| `rmdir <dir>`      | Remove an empty directory            |
| `rm <file>`        | Remove a file                        |
| `touch <file>`     | Create a new empty file              |
| `cp <src> <dest>`  | Copy file or directory               |
| `mv <src> <dest>`  | Move or rename file/directory        |
| `clear`            | Clear the terminal                   |

---

## 📖 Reading Files

| Command                        | Description                          |
|--------------------------------|--------------------------------------|
| `cat <file>`                   | View file contents                   |
| `less <file>`                  | View file page-by-page               |
| `more <file>`                  | View file page-by-page (older)       |
| `head <file>`                  | View the first 10 lines              |
| `tail <file>`                  | View the last 10 lines               |
| `tail -f <file>`               | Follow a file live (e.g., logs)      |

---

## 🔍 Find & Filter

| Command                                  | Description                               |
|------------------------------------------|-------------------------------------------|
| `find <path> -name "<pattern>"`          | Find files by name                        |
| `find <path> -type f -size +10M`         | Find files larger than 10MB               |
| `locate <file>`                          | Quickly locate a file                     |
| `whereis <command>`                      | Find binary/source/manual for a command   |
| `which <command>`                        | Show full path of shell command           |

---

## 🚦 Filtering & Searching (Grep)

| Command                            | Description                                   |
|------------------------------------|-----------------------------------------------|
| `grep "pattern" <file>`            | Search for pattern in file                    |
| `grep -r "pattern" <dir>`          | Recursive grep in directory                   |
| `grep -i "pattern"`                | Case-insensitive search                       |
| `grep -v "pattern"`                | Invert match                                  |
| `grep -n "pattern"`                | Show line numbers                             |
| `grep -A 3 -B 2 "pattern"`         | Show lines After/Before match                 |

---

## ✂️ Cut & Text Processing

| Command                             | Description                                    |
|-------------------------------------|------------------------------------------------|
| `cut -d':' -f1 /etc/passwd`         | Cut first field using colon as delimiter       |
| `cut -c1-5 <file>`                  | Cut first 5 characters from each line          |
| `awk '{print $1}' <file>`          | Print the first column                         |
| `sed 's/old/new/g' <file>`         | Replace text in a file                         |
| `tr 'a-z' 'A-Z' <file>`            | Translate lowercase to uppercase               |

---

## 📑 Sorting & Uniqueness

| Command                   | Description                                  |
|---------------------------|----------------------------------------------|
| `sort <file>`             | Sort lines in a file                         |
| `sort -r <file>`          | Reverse sort                                 |
| `sort -n <file>`          | Numerical sort                               |
| `uniq <file>`             | Remove duplicate lines                       |
| `uniq -c <file>`          | Count occurrences of each line               |
| `sort <file> | uniq`      | Combined sort and remove duplicates          |

---

## ⚙️ Advanced & System Info

| Command                    | Description                                  |
|----------------------------|----------------------------------------------|
| `top`                      | Real-time system resource usage              |
| `htop`                     | Interactive process viewer (enhanced top)    |
| `ps aux`                   | Show all running processes                   |
| `df -h`                    | Disk usage in human-readable format          |
| `du -sh <dir>`             | Size of a directory                          |
| `free -h`                  | Memory usage                                 |
| `uptime`                   | System uptime                                |
| `whoami`                   | Current user                                 |

---

## 🎯 Special & Misc Commands

| Command                      | Description                                   |
|------------------------------|-----------------------------------------------|
| `chmod +x <file>`            | Make a file executable                        |
| `chown user:group <file>`    | Change file ownership                         |
| `history`                    | Show command history                          |
| `alias ll='ls -la'`          | Create command alias                          |
| `echo $PATH`                 | Show system PATH variable                     |
| `man <command>`              | Show manual for a command                     |
| `exit`                       | Exit the terminal                             |

---

> 💡 Tip: Use `man <command>` or `command --help` for more details.

---

✅ **Feel free to contribute more commands via Pull Requests!**
