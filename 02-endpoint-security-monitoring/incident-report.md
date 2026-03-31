Incident Report — Authentication Failures and Account Creation
Summary

Multiple failed authentication attempts were detected on a monitored Linux endpoint, followed shortly by the creation of a new user account. The sequence of events may indicate password guessing activity followed by account creation for persistence.

Environment
Agent: endpoint-client
Operating System: Ubuntu Linux
Platform: Wazuh SIEM
Detection Details
Failed Authentication
Timestamp: Mar 31, 08:37:49
Rule: PAM: User login failed
Rule ID: 5503
Severity: 5
MITRE ATT&CK:
Tactic: Credential Access
Technique: T1110.001 (Password Guessing)
User: admin
