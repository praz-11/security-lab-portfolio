# Endpoint Security Monitoring and Incident Detection (Wazuh)

## Overview
This project demonstrates a basic SOC workflow using Wazuh SIEM to monitor endpoint activity, detect suspicious behaviour, and investigate security events. 

A Linux endpoint was connected to a Wazuh server, and controlled actions were performed to simulate potential attack activity. The resulting alerts were analysed to identify patterns consistent with credential access attempts and persistence techniques.

## Objectives
- Deploy a SIEM environment using Wazuh
- Connect an endpoint agent for log collection
- Generate and detect security-relevant events
- Analyse alerts using SOC-style investigation techniques
- Map observed behaviour to MITRE ATT&CK framework

## Lab Setup
- **SIEM Platform:** Wazuh (Manager, Indexer, Dashboard)
- **Endpoint:** Ubuntu Linux (Wazuh Agent installed)
- **Environment:** VirtualBox (NAT + Host-only networking)

---

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
- Alerts observed in Wazuh Threat Hunting module  
- Relevant events identified:
  - PAM authentication failures  
  - New user account creation  

### 4. Analysis
- Correlated failed login attempts with subsequent account creation  
- Mapped activity to MITRE ATT&CK techniques:
  - T1110.001 – Password Guessing  
  - T1136 – Create Account  

---

## Key Findings
- Repeated authentication failures were detected for a valid user account  
- A new user account was created shortly after failed login attempts  
- The sequence of events is consistent with a potential brute-force attempt followed by persistence activity  

---

## Skills Demonstrated
- SIEM deployment and configuration (Wazuh)
- Log analysis and alert triage
- Event correlation
- Basic threat detection
- MITRE ATT&CK mapping

---

## Files
- `setup.md` – Lab setup and configuration steps  
- `incident-report.md` – Detailed investigation and findings  
- `screenshots/` – Dashboard and event evidence  

---
