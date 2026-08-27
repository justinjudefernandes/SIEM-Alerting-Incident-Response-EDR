# SIEM Alerting, Incident Response & EDR

## 🎯 Objective:
Build an end-to-end security alerting and incident response workflow by integrating a ticketing system with the SIEM, automatically routing security detections into trackable tickets, and deploying Endpoint Detection and Response (EDR) to prevent malicious activity and contain compromised endpoints.

## 📊 Project Overview:
Deployed osTicket as a centralized incident ticketing system and integrated it with Elastic through API and webhook connectors, enabling detection rules to automatically generate tickets for analyst triage and investigation. Configured Windows brute force, SSH brute force, and Mythic C2 detection rules to route security alerts into osTicket, while developing a structured investigation methodology for analyzing brute force activity, validating indicators, and identifying suspicious activity following successful authentication. The project was extended with the deployment of Elastic EDR (Elastic Defend), which was validated through a controlled malicious payload download attempt. Elastic Defend successfully prevented the download, generated a prevention alert, and triggered an automated host isolation response, demonstrating an end-to-end:
        ```detection → alert → investigation → prevention → containment workflow```

## 🧰 Tools Used:
- Windows Server 2022
- XAMPP (Apache, MySQL, phpMyAdmin)
- osTicket (Ticketing System)
- Elastic Stack (Elasticsearch, Kibana)
- Elastic Detection Rules & Connectors
- Elastic EDR (Elastic Defend)
- Mythic C2 Framework
- PowerShell
- OSINT Tools (IOC/IP Reputation Research)

## 🛠️ Capabilities Demonstrated:
- Incident ticketing system deployment and administration
- Web server and database stack configuration
- SIEM-to-ticketing system integration using APIs and webhooks
- Automated alert-to-ticket workflows
- Security alert triage and incident investigation
- Brute force and SSH attack investigation
- C2 detection and alert handling
- IOC research and IP reputation analysis
- Endpoint Detection and Response (EDR) deployment and configuration
- Malware prevention and detection validation
- Automated endpoint containment and host isolation
- End-to-end detection-to-response workflow design

## 📁 Key Deliverables:
- Deployed and configured osTicket on a dedicated Windows Server
- Built the supporting Apache, MySQL, and phpMyAdmin environment using XAMPP
- Integrated osTicket with Elastic using an API key and webhook connector
- Verified automated ticket creation from SIEM-generated alerts
- Developed a repeatable methodology for investigating brute force activity
- Configured Windows brute force, SSH brute force, and Mythic C2 detection rules for automated ticket creation
- Validated alert-to-ticket workflows through controlled brute force and C2 simulations
- Deployed Elastic EDR (Elastic Defend) to a Windows endpoint
- Validated EDR prevention by blocking a controlled malicious payload download
- Configured an automated response action to isolate the affected endpoint
- Verified successful endpoint isolation and loss of network connectivity following a prevention alert

## 🔍 Steps Performed:

### 1. Ticketing System Research & Platform Deployment
- Researched the role of ticketing systems within security operations, including how platforms such as Jira, ServiceNow, and Freshdesk support alert tracking, incident management, accountability, and analyst workflows.
- Provisioned a Windows Server 2022 host and deployed XAMPP to provide the required Apache, MySQL, and phpMyAdmin environment.
- Configured Apache domain settings, phpMyAdmin connectivity, and firewall rules to support the ticketing platform.
- Installed osTicket, created and configured its supporting database, and completed the guided setup.
- Verified successful deployment by accessing the osTicket Staff Control Panel.

### 2. SIEM-to-Ticketing Integration
- Generated an API key within osTicket to authorize communication from the SIEM.
- Configured an Elastic connector using the osTicket API key to establish integration between Elastic and the ticketing platform.
- Built and configured a webhook connector to transmit alert information to osTicket in the required format.
- Generated a test SIEM alert and confirmed successful ticket creation and visibility within the osTicket Agent Panel.
- Validated the end-to-end workflow from SIEM detection through automated ticket creation.

### 3. Brute Force Investigation Methodology & Alert Routing
- Developed a structured investigation methodology for brute force alerts, focusing on:
  - Whether the source IP had a known malicious or suspicious history
  - Whether multiple user accounts were targeted
  - Whether any authentication attempts were successful
  - What activity occurred following successful authentication
  - Whether additional indicators suggested compromise or lateral movement
- Modified the Windows brute force detection rule to automatically route alerts into osTicket.
- Simulated brute force activity and verified that the resulting SIEM alert generated a corresponding investigation ticket.
- Applied IOC and IP reputation research to support alert validation and investigation.

### 4. SSH & C2 Detection Rule Alert Routing
- Configured the SSH brute force detection rule to automatically forward alerts into osTicket.
- Performed controlled SSH brute force simulations and verified successful alert-to-ticket generation.
- Configured the Mythic C2 detection rule to automatically route C2 alerts into osTicket.
- Validated the workflow through controlled C2 activity and confirmed that the resulting detection generated a trackable incident ticket.
- Applied timeline-building and event correlation techniques to support investigation of routed alerts.

### 5. Endpoint Detection & Response (EDR) Deployment & Validation
- Installed and configured Elastic EDR (Elastic Defend) on the Windows endpoint.
- Initiated a controlled malicious payload download attempt from the Mythic C2 infrastructure to validate endpoint protection.
- Confirmed that Elastic Defend successfully prevented the malicious payload download and generated a malware prevention alert.
- Verified that the blocked activity was visible and traceable within Elastic Discover.
- Configured an automated response action to isolate the endpoint following a Malware Prevention Alert.
- Repeated the controlled download attempt while monitoring endpoint connectivity through continuous ping testing.
- Confirmed that the prevention alert triggered the automated response and isolated the endpoint, resulting in loss of network connectivity.
- Validated the complete **detection → prevention → automated response → endpoint isolation** workflow.
