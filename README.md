# 🛡️ SSH Log Threat Detection Using Splunk Cloud

This project documents a hands-on security operations task I completed during my SOC onboarding. The objective was to simulate a real-world threat-hunting exercise by ingesting and analyzing **OpenSSH logs** in **Splunk Cloud** to identify suspicious behavior, investigate anomalies, and implement proactive detection mechanisms.

---

## 🚀 Overview

I used **Splunk Cloud** to upload and analyze SSH logs, detect brute-force login attempts, isolate suspicious IP addresses, and create dashboards and alerts for continuous monitoring. I also configured user management, enforced security policies, and performed custom field extractions to enrich the analysis.

---

## 🎯 Objectives

- Ingest and analyze OpenSSH log files for unusual or malicious activity  
- Detect anomalies such as brute-force attacks and invalid login attempts  
- Create users in Splunk Cloud with appropriate access control  
- Design a dashboard to visualize suspicious events  
- Configure scheduled alerts for recurring high-risk behavior  
- Extract custom fields (e.g., source IP) to improve search and detection  

---

## 🔐 User Management in Splunk Cloud

To simulate a multi-user SOC environment:

- I created users with roles like `admin`, `power`, and `user`
- Enforced password policies (e.g., change on first login)
- Configured default apps and time zones (WAT)
- Applied role-based access controls following the principle of least privilege

---

## 📁 Log File Ingestion

- Uploaded OpenSSH log using the **"Add Data"** interface in Splunk
- Verified proper parsing and source type selection
- Indexed data into the `main` index for analysis

---

## 🔍 SSH Log Analysis Approach

My analysis focused on detecting:

- Repeated login failures and invalid user attempts
- Disconnects before authentication (`preauth`)
- IPs associated with known malicious activity (verified via VirusTotal)
- Time-based anomalies and patterns indicative of brute-force attacks

---

## ⚠️ Key Findings

### 🚩 Malicious IPs Detected
The following IP addresses were flagged as malicious or suspicious:
- `5.188.10.180`
- `187.141.143.180` (flagged on VirusTotal)
- `103.207.39.212`

### ❌ Brute-Force Behavior
Patterns observed:
- Multiple failed passwords and invalid usernames
- Repeated `Received disconnect [preauth]` events
- Break-in attempts suggesting automated scripts

### ✅ Legitimate Access
One IP, `119.137.64.142`, successfully authenticated. It was verified as a legitimate access point, likely belonging to an authorized user.

---

## 📊 Dashboard & SIEM Alert

- Created a Splunk dashboard to monitor SSH disconnects from IP `112.95.230.3`
- Configured an **automated alert** to:
  - Trigger daily at 8:00 AM
  - Fire when more than 2 events are detected
  - Send email alerts in plain text format
  - Restrict delivery to a specific domain (e.g., Gmail)

---

## 🧩 Field Extraction

To enhance parsing and investigation, I created a custom field extraction:

- **Target Field:** `src_ip`  
- **IP Address Tagged:** `183.62.140.253`  
- **Use Cases:**  
  - Enables more precise search queries  
  - Can be reused in dashboards and alerts  
  - Integrates with threat intelligence feeds

---

## 🧠 Skills Demonstrated

- Threat hunting using Splunk Cloud  
- Log ingestion and parsing  
- User and role configuration  
- Alert creation and monitoring  
- Regex-based field extraction  
- IOC detection and analysis  

---

🖼️ See the [Wiki]((https://github.com/Deeoojo/splunk-integration/wiki)) for screenshots
