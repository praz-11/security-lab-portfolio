# Lab Setup and Configuration

## Environment
- Platform: VirtualBox
- SIEM Server: Ubuntu Linux (Wazuh Manager, Indexer, Dashboard)
- Endpoint: Ubuntu Linux (Wazuh Agent)

## Network Configuration
Two network adapters were configured on both virtual machines:

- Adapter 1: NAT (internet access)
- Adapter 2: Host-only Adapter (internal communication)

This allowed:
- Internet access for installation
- Direct communication between SIEM and endpoint

## Wazuh Installation (SIEM Server)
Wazuh was installed using the official quickstart method:

- Installed Wazuh Manager, Indexer, and Dashboard
- Verified services were running:
  - wazuh-manager
  - wazuh-indexer
  - wazuh-dashboard

Accessed dashboard via:
https://localhost

## Agent Installation (Endpoint)
Wazuh agent was installed on the endpoint system and configured to connect to the SIEM server.

- Set WAZUH_MANAGER to the SIEM server’s internal IP (host-only network)
- Updated agent configuration file (`ossec.conf`) with correct manager IP
- Started and enabled the agent service

## Verification
- Agent successfully registered in Wazuh dashboard
- Status confirmed as "Active"
- Logs from endpoint visible in Threat Hunting module

--
