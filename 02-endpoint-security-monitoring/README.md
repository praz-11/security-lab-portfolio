# Endpoint Security Monitoring and Incident Detection (Wazuh)

## Overview
This project uses Wazuh to monitor endpoint activity, detect suspicious behaviour, and investigate security events.

A Linux endpoint was connected to a Wazuh server, where authentication failures and account creation events were generated and analysed. The resulting alerts were reviewed to understand how individual events relate to potential credential access and persistence activity.

## Objectives
- Deploy a SIEM environment using Wazuh
- Connect an endpoint agent for log collection
- Generate and detect security-relevant events
- Analyse alerts and identify patterns across events
- Map observed behaviour to the MITRE ATT&CK framework

## Lab Setup
- **SIEM Platform:** Wazuh (Manager, Indexer, Dashboard)
- **Endpoint:** Ubuntu Linux (Wazuh Agent installed)
- **Environment:** VirtualBox (NAT + Host-only networking)

## Key Activities

### 1. Agent Deployment
- Installed Wazuh agent on endpoint system  
- Configured agent to communicate with Wazuh manager  
- Verified agent connection via dashboard  

### 2. Event Simulation
The following actions were performed on the endpoint:

- Multiple failed authentication attempts using `sudo`
- Creation of a new user account (`attackeruser`)

### 3. Detection and Monitoring
- Alerts observed in the Wazuh Threat Hunting module  
- Relevant events identified:
  - PAM authentication failures  
  - New user account creation  

### 4. Analysis
- Correlated failed login attempts with subsequent account creation  
- Mapped activity to MITRE ATT&CK techniques:
  - T1110.001 – Password Guessing  
  - T1136 – Create Account  

## Key Findings
- Repeated authentication failures were detected for a valid user account  
- A new user account was created shortly after failed login attempts  
- The sequence of events is consistent with a potential brute-force attempt followed by persistence activity  

## Skills Demonstrated
- SIEM deployment and configuration (Wazuh)
- Log analysis and alert triage
- Event correlation
- Threat detection
- MITRE ATT&CK mapping

## Additional Observations
Authentication failures were observed prior to account creation. While this was a controlled scenario, similar patterns in a production environment could indicate brute-force activity followed by persistence.

To improve detection capability:
- Implement correlation rules to flag sequences of failed logins followed by account creation  
- Configure thresholds for repeated authentication failures  
- Extend monitoring to include privilege escalation activity  

## Files
- `setup.md` – Lab setup and configuration steps  
- `incident-report.md` – Detailed investigation and findings  
- `screenshots/` – Dashboard and event evidence  
