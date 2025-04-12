# 🔐 Hash Cracking with John the Ripper - Learning Log

## 🧠 What I Learned

In this exercise, I explored how password hashes work, especially **MD5**, and how they can be cracked using tools like **John the Ripper**. 
I learned how to identify hash formats, use custom rules, and understand the importance of strong password policies.

This task helped me understand the offensive perspective of password cracking, which is essential knowledge for defenders in a SOC environment.

---

## 📚 Topics Covered

- Hash functions: What they are and why they're used
- MD5: Fast, outdated, and vulnerable to brute-force
- John the Ripper: Basic usage for cracking hashes
- Custom wordlists and rule-based cracking
- Importance of hash format recognition

---

## 🛠️ Tools Used

- `John the Ripper`
- `hash-identifier`
- `rockyou.txt` wordlist
- Custom rule files for John (`--rules`)

---

## 🔍 Example Workflow
Used hashid to detect: MD5
john --format=raw-md5 hash.txt --wordlist=/usr/share/wordlists/rockyou.txt

## 📸 Screenshots

![Event ID 4625](images/John-Hash-Password.png)
