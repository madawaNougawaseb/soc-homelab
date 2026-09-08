# SOC Homelab

## 1. Project Description

A hands-on Security Operations Center (SOC) homelab designed to simulate a small enterprise environment and provide practical experience in security monitoring, detection engineering, threat hunting, incident investigation, and incident response.

## 2. Project Objectives

* Build a functional SOC environment.
* Deploy and configure a Security Information and Event Management (SIEM) platform.
* Collect and analyze endpoint and network telemetry.
* Simulate realistic cyber attacks.
* Develop and test security detections.
* Investigate security alerts.
* Perform basic threat hunting.
* Practice incident response procedures.
* Document security incidents professionally.
* Map attack activity to the MITRE ATT&CK framework.

## 3. Scope

The lab will contain isolated virtual machines representing attackers, servers, endpoints, and SOC infrastructure.

The environment will be designed so that attacks can be safely simulated without exposing the real home network.

## 4. Learning Goals

This project will be used to develop practical skills in:

* SOC operations
* SIEM administration
* Log analysis
* Security monitoring
* Detection engineering
* Threat hunting
* Incident response
* Network security
* Endpoint security
* Windows security
* Linux security
* MITRE ATT&CK
* Security documentation

## 5. Technologies

Technologies will be selected and documented during the implementation phase.

Initial candidates include:

* VMware Workstation
* Windows
* Linux
* Kali Linux
* Wazuh
* Sysmon
* Wireshark
* Nmap
* MITRE ATT&CK

## 6. Lab Environment

The virtual lab will use an isolated network separate from the normal home network.

The final architecture, IP addressing scheme, virtual machines, and network configuration will be documented in the architecture documentation.

## 7. Security Architecture

The SOC will contain separate components for:

* Attack simulation
* Endpoints
* Servers
* Security monitoring
* Log collection
* Detection
* Investigation
* Response

The final architecture diagram will be stored in:

`/diagrams/`

## 8. Attack Scenarios

The project will progressively introduce controlled attack scenarios.

Examples may include:

* Network reconnaissance
* Port scanning
* Brute-force attacks
* PowerShell activity
* Credential attacks
* Suspicious process execution
* Privilege escalation
* Persistence
* Malware simulation

All attacks will be conducted only within the isolated lab environment.

## 9. Detection Strategy

Security detections will be developed based on observed attack behavior and available telemetry.

Each detection will document:

* Detection objective
* Data source
* Attack technique
* Detection logic
* Alert
* Investigation process
* False-positive considerations
* MITRE ATT&CK mapping

## 10. Incident Response

Detected incidents will follow a basic incident-response workflow:

1. Identification
2. Investigation
3. Containment
4. Eradication
5. Recovery
6. Lessons learned

Incident reports will be stored in:

`/incident-reports/`

## 11. Evidence Collection

Evidence collected during the project may include:

* Screenshots
* Network diagrams
* SIEM alerts
* Log samples
* Detection rules
* Investigation notes
* Incident reports
* Configuration files
* Scripts

Sensitive information such as credentials, API keys, private keys, and real network information will never be published.

## 12. Future Improvements

Potential future improvements include:

* Additional endpoints
* Active Directory
* Network IDS/IPS
* Vulnerability management
* Threat intelligence
* Cloud security
* Automated response
* Advanced threat hunting
* Digital forensics
