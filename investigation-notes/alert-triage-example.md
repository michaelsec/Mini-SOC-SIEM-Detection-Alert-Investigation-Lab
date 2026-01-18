# Alert Triage Example – Failed Login Attempts

## Alert Information
- Alert Name: Multiple Failed Login Attempts  
- Severity: Medium  
- Detection Rule: Failed Login Detection  
- Time Detected: 2026-01-18 14:32:10 UTC  
- Source: SIEM (ELK/Wazuh)

---

## Alert Details
| Field        | Value            |
|-------------|------------------|
| Username    | jdoe             |
| Source IP  | 192.168.1.50     |
| Attempts   | 8 failed logins  |
| Timeframe  | 2 minutes        |
| Log Source | Windows Security |

Windows Event ID: **4625** (Failed Logon)

---

## Triage Process

1. Verified the alert was generated from a valid log source  
2. Confirmed multiple failed authentication attempts in a short time window  
3. Checked if source IP was:
   - Internal network: **Yes**
   - Known user device: **Unknown**
4. Reviewed if any successful login followed the failures:
   - Result: **No successful logins found**
5. Checked for:
   - Account lockout: **Not yet triggered**
   - Endpoint alerts: **None**
6. Pattern suggests:
   - Possible brute-force or password guessing attempt

---

## Assessment
| Category | Result |
|--------|-------|
| Threat Level | Suspicious |
| Likely Cause | Credential guessing or misconfigured service |
| False Positive | Unlikely |

---

## Actions Taken
- Escalated alert to senior analyst  
- Documented findings in ticketing system  
- Recommended:
  - Temporary account lock
  - Source IP monitoring or blocking

---

## Final Status
**Escalated for further investigation**

---

## Notes
This alert demonstrates standard SOC triage workflow:
- Validate alert  
- Gather context  
- Determine legitimacy  
- Escalate with evidence  
- Document clearly  
