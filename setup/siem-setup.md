# SIEM Setup – Mini SOC Lab

## Objective
Build a small SIEM environment to simulate real SOC workflows:
- Log ingestion  
- Detection creation  
- Alert triage  
- Incident investigation  

Using:
- ELK Stack / Wazuh  
- Windows VM  
- Linux VM  

---

## Environment

| Component | Purpose |
|--------|-------|
| ELK / Wazuh Server | Central log collection and alerting |
| Windows VM | Generate authentication and security logs |
| Linux VM | Generate auth and sudo activity logs |

---

## Step 1 – SIEM Installation
- Deployed Wazuh with ELK on a Linux server  
- Verified access to:
  - Kibana dashboard  
  - Wazuh manager  
  - Indexing services  

---

## Step 2 – Agent Setup

### Windows Agent
- Installed Wazuh agent  
- Configured:
  - Security Event Logs
  - Authentication logs
- Verified:
  - Event ID 4624 (Successful logon)
  - Event ID 4625 (Failed logon)

### Linux Agent
- Installed Wazuh agent  
- Monitored:
  - `/var/log/auth.log`
  - sudo activity
  - SSH login attempts  

---

## Step 3 – Log Validation

Confirmed:
- Windows logs appearing in SIEM  
- Linux logs being indexed  
- Timestamps and hostnames accurate  

Used:
- Test failed login attempts  
- Test sudo usage  
- SSH login failures  

---

## Step 4 – Detection Rules Created

| Detection | Purpose |
|--------|-------|
| Failed Login Detection | Identify password guessing behavior |
| Brute Force Detection | Detect automated attacks |
| Privilege Escalation Detection | Monitor high-risk account actions |

---

## Step 5 – Alert Testing

Simulated:
- Multiple failed logins from Windows  
- Multiple usernames from same IP  
- sudo privilege escalation  

Verified:
- Alerts triggered correctly  
- Logs linked to alerts  
- Severity assigned properly  

---

## Step 6 – Investigation Workflow

Each alert followed:
1. Alert validation  
2. Log review  
3. Context gathering  
4. Threat assessment  
5. Documentation  
6. Escalation decision  

---

## Outcome
This setup replicates:
- Entry-level SOC monitoring environment  
- Alert triage process  
- Investigation documentation  
- Detection engineering basics  
