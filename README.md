# 🔍 Penetration Tester – Capstone Project

**Advanced Executive Program in Cybersecurity**  
**Virtual Internship Project – IIIT Bangalore**

## 👤 Submitted by:
**Deepak Sharma**

---

## 🧾 Project Overview

This project simulates a real-world **gray-box penetration test** for **El Banco Bank**, one of the fastest-growing banks in Europe managing over €200 billion in assets. As a penetration tester, the objective is to **identify vulnerabilities across multiple systems**, starting from reconnaissance to exploitation planning.

---

## ⚙️ Lab Environment

- 🔹 Kali Linux (attacker)
- 🔹 Ubuntu Server
- 🔹 Windows 10
- 🔹 WebGoat (vulnerable web app)
- 🔹 AWS-hosted virtual lab network

---

## ✅ Tasks Performed

### 🔹 Task 1 – Half-Open SYN Scan

| Objective | Perform a stealthy TCP SYN scan to identify open ports |
|-----------|----------------------------------------------------------|
| Tool Used | Nmap (`-sS -T4 -Pn`)                                     |
| Outcome   | Identified open TCP ports on Ubuntu, WebGoat, and Windows targets |

**Sample Command:**
```bash
nmap -sS -T4 -Pn -oN output.txt <target-ip>

🔹 Results Summary:
| Target System | IP Address    | Open Ports                 |
| ------------- | ------------- | -------------------------- |
| Ubuntu        | 172.31.6.190  | 22 (SSH), 8443 (HTTPS-alt) |
| WebGoat       | 172.31.14.129 | 22 (SSH), 80 (HTTP), 8443  |
| Windows 10    | 172.31.12.236 | 3389 (RDP), 5357, 8443     |

🔹 Task 2 – Aggressive Scan

| Objective  | Perform OS detection, version detection, script scanning, and traceroute |
| ---------- | ------------------------------------------------------------------------ |
| Tool Used  | Nmap (`-A -T4 -Pn`)                                                      |
| Key Output | Identified OS, services, versions, and SSL/TLS certificate info          |

Findings:

WebGoat: Linux, nginx, expired cert on port 8443

Windows 10: RDP and HTTPAPI exposed, valid cert

Ubuntu: NICE DCV over 8443 with expired SSL certificate

🔹 Task 3 – Web Log Attack Analysis

| Log # | Attack Type          | Description                           | Mitigation                        |
| ----- | -------------------- | ------------------------------------- | --------------------------------- |
| 1     | DOM-Based XSS        | JavaScript executes from URL fragment | Input sanitization, CSP           |
| 2     | Directory Traversal  | Attempts to access `/etc/passwd`      | Whitelist paths, input validation |
| 3     | SQL Injection (SQLi) | Injected SQL logic into query         | Use prepared statements, WAF      |

Decoded Attack Payloads:

| Log # | Payload Example                       | Attack Type         |
| ----- | ------------------------------------- | ------------------- |
| 1     | `javascript:domxssExecutionSink(...)` | DOM-Based XSS       |
| 2     | `/../../../../etc/passwd`             | Directory Traversal |
| 3     | `'AND 1=cast(...) or '1'='`           | SQL Injection       |

🛡️ Key Tools Used
🔧 nmap for scanning

🧪 bash, openssl, whois, and encoder/decoder tools

📜 Manual analysis of log files

🧱 WebGoat for vulnerability emulation


✅ Outcome
The project demonstrates:

Effective use of network scanning and enumeration

Ability to analyze suspicious traffic and identify attacks

Application of real-world mitigation strategies

📄 License
This repository is a submission for the Advanced Executive Program in Cybersecurity and is intended for academic and professional learning purposes.
