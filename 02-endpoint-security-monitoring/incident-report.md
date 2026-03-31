# Incident Report: Authentication Failures and Account Creation

## Summary
Multiple failed authentication attempts were detected on a monitored Linux endpoint, followed shortly by the creation of a new user account. The sequence of events suggests a potential password guessing attempt followed by account creation for persistence.

## Environment
- Agent: endpoint-client  
- Operating System: Ubuntu Linux  
- Monitoring Platform: Wazuh SIEM  

## Detection Details

### Failed Authentication
- Timestamp: Mar 31, 08:37:49  
- Rule: PAM: User login failed  
- Rule ID: 5503  
- Severity Level: 5  
- MITRE ATT&CK:
  - Tactic: Credential Access  
  - Technique: T1110.001 (Password Guessing)  
- User: admin  

**Log:**
Mar 31 08:37:49 endpoint-client sudo[6767]: pam_unix(sudo:auth): authentication failure; logname=admin uid=1000 euid=0 tty=/dev/pts/0 ruser=admin rhost= user=admin

### User Account Creation
- Timestamp: Mar 31, 08:38:44  
- Rule: New user added to the system  
- Rule ID: 5902  
- Severity Level: 8  
- MITRE ATT&CK:
  - Tactic: Persistence  
  - Technique: T1136 (Create Account)  
- User Created: attackeruser  

**Log:**
Mar 31 08:38:44 endpoint-client useradd[6781]: new user: name=attackeruser, UID=1001, GID=1001, home=/home/attackeruser, shell=/bin/bash

## Analysis
The logs show repeated failed authentication attempts for the `admin` account, followed by the creation of a new user account within a short time window. This pattern is consistent with a potential password guessing attempt followed by account creation.

There is no direct confirmation of successful authentication; however, the sequence of events indicates behaviour that warrants further investigation.

## Impact
- Possible unauthorized access attempt  
- New account introduces persistence risk  
- Potential for further misuse or privilege escalation  

## Recommendations
- Remove or disable the `attackeruser` account  
- Reset credentials for affected users  
- Review authentication logs for additional suspicious activity  
- Implement account lockout policies  
- Consider multi-factor authentication where applicable  
