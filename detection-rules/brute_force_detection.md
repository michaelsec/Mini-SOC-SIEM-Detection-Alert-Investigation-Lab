# Brute Force Login Detection Rule

## Name
Brute Force Attack – Multiple Users From Single IP

## Purpose
Detect automated attacks where one source attempts to log into multiple user accounts in a short time.

## Data Sources
- Windows Security Logs  
- Linux Authentication Logs  
- SIEM: ELK / Wazuh  

## Relevant Log Fields
- Source IP  
- Username  
- Timestamp  
- Authentication Result  

---

## Detection Logic

Trigger an alert when:
- One IP attempts logins against **3 or more different usernames**
- Within **2 minutes**
- All or mostly failed attempts

Pseudo logic:
IF unique(username) >= 3
AND count(failed_logins) >= 6
AND timeframe <= 2 minutes
GROUP BY source_ip
THEN trigger alert

---

## Severity
High

---

## Why This Matters
This is a strong indicator of:
- Automated brute force tools  
- Credential harvesting  
- External attack behavior  

It typically warrants:
- Immediate investigation  
- IP blocking  
- Account protection actions  

---

## Investigation Steps

1. Identify source IP  
2. Check if:
   - IP is external  
   - Known malicious or not  
3. Review targeted usernames  
4. Look for:
   - Successful logins after failures  
5. Correlate with:
   - Firewall logs  
   - Endpoint alerts  
6. Escalate to senior analyst or incident response if confirmed  

---

## Example Alert
Alert: Brute Force Login Behavior
Source IP: 45.92.18.33
Users Targeted: admin, jsmith, hr_user
Failed Attempts: 12 in 2 minutes
Severity: High
