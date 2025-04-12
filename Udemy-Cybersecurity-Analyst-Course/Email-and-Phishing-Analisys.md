# 📧 Phishing Email Analysis - Triage & Tools

## 🧠 What I Learned

In this task, I learned how to analyze suspicious emails by reviewing the **headers, body content, and attachments**. I used tools like **Sublime Text** for deep inspection and **MXToolbox** for checking sender infrastructure and domain reputation. This hands-on experience helped me understand how attackers spoof emails and how SOC analysts detect them.

---

## 📚 Topics Covered

- Email header dissection (Received paths, Return-Path, SPF/DKIM)
- Decoding obfuscated links in email bodies
- Attachment inspection (e.g., `.html`, `.pdf`, `.docm`)
- Identifying phishing attempts through URL and language analysis
- Using **MXToolbox** to validate sender domains and IPs
- Manual triage using **Sublime Text** for raw email files

---

## 🛠️ Tools Used

- **Sublime Text**: for reviewing `.eml` and `.msg` raw email formats
- **MXToolbox**: for checking DNS records, SPF failures, blacklist hits

---

## 🔍 Sample Investigation Steps

1. Opened email file in Sublime Text to view full raw headers
2. Verified SPF/DKIM/DMARC results
3. Identified suspicious sender domain using `MXToolbox`
4. Extracted and decoded malicious link inside HTML body
5. Flagged an attached file that used an `.html` redirect to a fake login page

---

## 📸 Screenshot

![Header Analysis in Sublime](../images/phishing-header-sublime.png)


