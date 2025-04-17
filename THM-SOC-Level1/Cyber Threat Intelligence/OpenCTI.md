# 🪟 OpenCTI - TryHackMe Room Writeup

## 🧠 What I Learned

### **[OpenCTI](https://github.com/OpenCTI-Platform/opencti) is another open-sourced platform designed to provide organisations with the means to manage CTI through the storage, analysis, visualisation and presentation of threat campaigns, malware and IOCs.**
- What is OpenCTI and how is it used?
- How would I navigate through the platform?
- What functionalities will be important during a security threat analysis?

---

## 📚 Topics Covered

- ### OpenCTI Data Model:
  - OpenCTI uses a variety of knowledge schemas in structuring data, the main one being the Structured Threat Information Expression [(STIX2)](https://oasis-open.github.io/cti-documentation/stix/intro) standards
  - ![OpenCTI Data Model](../../images/OpenCTIModel.png)
  
---

## 🛠️ Tools Used

- OpenCTI
- TryHackMe interactive lab environment
  
---

## 🔍 Investigative Scenario

As a SOC analyst, you have been tasked with investigations on malware and APT groups rampaging through the world. Your assignment is to look into the CaddyWiper malware and APT37 group. Gather information from OpenCTI to answer the following questions.
  - What is the earliest date recorded related to CaddyWiper?  Format: YYYY/MM/DD
  - ![OpenCTI Task](../../images/OpenCTI-Screenshots/OpenCTI-Task-1-01.png)
  - Which Attack technique is used by the malware for execution?
  - ![OpenCTI Task](../../images/OpenCTI-Screenshots/OpenCTI-Task-1-02.png)
  - How many malware relations are linked to this Attack technique?
  - ![OpenCTI Task](../../images/OpenCTI-Screenshots/OpenCTI-Task-1-03.png)
  - Which 3 tools were used by the Attack Technique in 2016? (Ans: Tool1, Tool2, Tool3)
  - ![OpenCTI Task](../../images/OpenCTI-Screenshots/OpenCTI-Task-1-04.png)
  - What country is APT37 associated with?
  - ![OpenCTI Task](../../images/OpenCTI-Screenshots/OpenCTI-Task-1-05.png)
  - Which Attack techniques are used by the group for initial access? (Ans: Technique1, Technique2)
  - ![OpenCTI Task](../../images/OpenCTI-Screenshots/OpenCTI-Task-1-06.png)

---

## ✅ Status: Completed

