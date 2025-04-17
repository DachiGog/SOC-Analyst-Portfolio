# 🪟 MISP - Malware Information Sharing Platform - TryHackMe Room Writeup

## 🧠 What I Learned

- Introduction to MISP and why it was developed.
- Use cases MISP can be applied to
- Core features and terminologies.
- Dashboard Navigation.
- Event Creation and Management.
- Feeds and Taxonomies.

---

## 📚 Topics Covered

- 🔺 Pyramid Of Pain:
  - Understanding the Pyramid of Pain concept as a Threat Hunter, Incident Responder, or SOC Analyst is important.

- 🔗 Cyber Kill Chain
  - learn about each phase of the Cyber Kill Chain Framework, the advantages and disadvantages of the traditional Cyber Kill Chain. 
 
- ⛓️ Unified Kill Chain
  - Understanding why frameworks such as the UKC are important and helpful in establishing a good cybersecurity posture
  - Using the UKC to understand an attacker's motivation, methodologies and tactics
  - Understanding the various phases of the UKC
  - Discover that the UKC is a framework that is used to complement other frameworks such as MITRE.

- 💠 Dimond Model
  - Identify the elements of an intrusion. 
  - Create a Diamond Model for events such as a breach, intrusion, attack, or incident. 
  - Analyze an Advanced Persistent Threat (APT). 

- Introduction to MITRE
  - Focus on other projects/research that the US-based non-profit MITRE Corporation has created for the cybersecurity community, specifically:
    - ATT&CK ®  ( A dversarial  T actics,  T echniques,  and   C ommon  K nowledge) Framework
    - CAR ( C yber  A nalytics  R epository) Knowledge Base
    - ENGAGE  (sorry, not a fancy acronym)
    - D3FEND ( D etection,  D enial, and  D isruption  F ramework  E mpowering  N etwork  D efense)
    - AEP ( A TT&CK  E mulation  P lans)
    
- Mapping logs to MITRE ATT&CK (Initial Access, Execution)
  -   

---

## 🛠️ Tools Used

- Windows Event Viewer
- TryHackMe interactive lab environment
- MITRE ATT&CK framework
- MITRE Cyber Analytics Repository
- MITRE ENGAGE Matrix
- MITRE D3FEND Matrix
- MITRE AEP Matrix

---

## 🔍 Scenario Task

CIRCL (Computer Incident Respons Center Luxembourg) published an event associated with PupyRAT infection. Your organisation is on alert for remote access trojans and malware in the wild, and you have been tasked to investigate this event and correlate the details with your SIEM. Use what you have learned from the room to identify the event and complete this task.
  - What event ID has been assigned to the PupyRAT event?
  - ![Task Screen 1](../images/MISP/MISP-Task-1.png)
  - The event is associated with the adversary gaining ______ into organisations.
  - ![Task Screen 2](../images/MISP/MISP-Task-2.png)
  - What IP address has been mapped as the PupyRAT C2 Server#
  - ![Task Screen 3](../images/MISP/MISP-Task-3.png)
  
---

## ✅ Status: Completed

🔗 [TryHackMe Room Link]((https://tryhackme.com/room/mitre))  
🕒 Time Spent: ~3 hours

# 🏛️ Pyramid Challenge - TryHackMe

## 🧩 Challenge Type
This was an investigative-style challenge that tested my ability to **dig into provided data** to find clues, decode information, and piece together a series of answers — similar to a **CTF-style triage puzzle**.

It required:
- Careful attention to detail
- Pattern recognition
- Logical thinking and patience

---

## 🔍 What I Did

- Explored the file closely for **hidden information**
- Used **online tools and manual inspection** to find embedded clues (metadata, steganography, filenames)
- Followed a trail of subtle hints and decoded messages to uncover the correct answers
- Each correct answer led to the next layer of the investigation

---

## 🧠 What I Learned

- How to approach investigative challenges methodically
- How small clues (like filenames or metadata) can be critical in investigations
- Importance of documenting each step and hypothesis
- How real-world triage can involve creative problem-solving, not just tool usage

---

## 💡 Skills Demonstrated

- Analytical thinking
- Attention to detail
- Basic steganography and OSINT-style investigation
- Persistence in multi-layered challenges

---

## 📌 Takeaways

This challenge was a great reminder that not all investigations are technical — some rely on mindset. It strengthened my **SOC investigation workflow**, including documentation, checking assumptions, and breaking down abstract problems.

---

✅ Status: Completed  
🕒 Time spent: ~1 hour  
