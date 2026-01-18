# Failed Login Detection Rule

## Name
Multiple Failed Login Attempts – Single User

## Purpose
Detect repeated failed authentication attempts that may indicate password guessing, brute force activity, or account misuse.

## Data Sources
- Windows Security Event Logs  
- Linux Authentication Logs  
- SIEM: ELK / Wazuh  

## Relevant Log Fields
- Username  
- Source IP  
- Timestamp  
- Event ID  
- Failure Reason  

### Windows Example
- Event ID: 4625 (Failed Logon)

### Linux Example
- `/var/log/auth.log`
- Message containing: `Failed password`

---

## Detection Logic

Trigger an alert when:
- More than **5 failed login attempts**
- From the **same IP or same username**
- Within **2 minutes**

Pseudo logic:

IF count(failed_logins) > 5
AND timeframe <= 2 minutes
GROUP BY username OR source_ip
THEN trigger alert

---

## Severity
Medium

---

## Why This Matters
Repeated failed login attempts are one of the earliest signs of:
- Brute force attacks  
- Credential stuffing  
- Compromised accounts  

Detecting this early allows analysts to:
- Lock accounts  
- Block IPs  
- Prevent successful compromise

---

## Investigation Steps

1. Verify alert source and log type  
2. Check:
   - Username targeted  
   - Source IP  
   - Attempt frequency  
3. Determine:
   - Internal vs external IP  
   - User mistake vs attack pattern  
4. Check if:
   - Account locked  
   - Successful login followed failures  
5. Escalate if suspicious  
6. Document findings  

---

## Example Alert

Alert: Multiple Failed Login Attempts
User: jdoe
Source IP: 192.168.1.50
Attempts: 8 in 2 minutes
Severity: Medium
