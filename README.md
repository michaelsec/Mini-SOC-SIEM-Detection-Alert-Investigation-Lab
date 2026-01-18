# Mini-SOC-SIEM-Detection-Alert-Investigation-Lab
This project simulates a small Security Operations Center environment. It demonstrates how to collect logs, create detection rules, triage alerts, and investigate suspicious activity using a SIEM. The focus is on defensive monitoring and SOC workflows.

Tools:
ELK/Wazuh, Windows, Linux

Logs used:
Windows authentication logs
Linux auth logs
Network traffic

Detections:
Failed login detection
Brute-force login detection
Privilege escalation detection


Core Project Tasks:

Detection 1 – Failed Login Alert
Trigger when:
More than 5 failed logins in 2 minutes
Same username or same IP

Document:
What log field you used
Why this matters
Example screenshot

Detection 2 – Brute Force Behavior
Trigger when:
Multiple usernames from one IP
Short time window

Detection 3 – Privilege Escalation
Trigger when:
Windows Event ID 4672
Or sudo usage in Linux logs
