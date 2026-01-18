# Mini SOC Lab – SIEM Detection & Alert Investigation

This project simulates a small Security Operations Center (SOC) environment.  
It demonstrates how logs are collected, detections are created, alerts are triaged, and investigations are documented using a SIEM.

The goal is to show real SOC workflows, not just tool usage.

---

## What This Project Shows
- SIEM log ingestion and monitoring  
- Detection engineering fundamentals  
- Alert triage and investigation  
- Incident documentation  
- Defensive security mindset  

---

## Tools Used
- ELK Stack / Wazuh  
- Windows VM  
- Linux VM  

---

## Log Sources
- Windows Security Event Logs (Event ID 4624, 4625, 4672)  
- Linux Authentication Logs (`/var/log/auth.log`)  
- SSH and sudo activity  

---

## Detections Implemented

| Detection | Description |
|--------|------------|
| Failed Login Detection | Detects repeated authentication failures against a single account |
| Brute Force Detection | Detects multiple usernames being attacked from a single IP |
| Privilege Escalation Detection | Detects high-risk privilege usage (Windows & Linux) |

Detection documentation:
- `detection-rules/failed_login_detection.md`
- `detection-rules/brute_force_detection.md`

---

## Example Investigation
A full SOC-style alert triage example can be found here:
investigation-notes/alert-triage-example.md
