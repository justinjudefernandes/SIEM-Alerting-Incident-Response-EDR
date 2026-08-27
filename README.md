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

### 1. Ticketing System Research & Web Server Environment Setup

- Researched the role of ticketing systems within security operations, including how platforms such as Jira, ServiceNow, and Freshdesk support alert tracking, incident management, accountability, and analyst workflows.
- Provisioned a Windows Server 2022 host and deployed XAMPP to establish the required Apache, MySQL, and phpMyAdmin environment.
- Configured Apache domain settings, phpMyAdmin connectivity, and firewall rules to support the ticketing platform.

📌 Refer to the below screenshots: (left to right)

<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/cca0080f-23bb-485a-b77c-c1977e5b83f0" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/5b9a27a2-140f-4a7d-a1cd-be7787a73d68" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/087dfc17-5dac-4ab0-b39e-2e5fa67c5673" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/bf396bcc-fdfa-48de-9c31-3131444773c9" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/10ea2dc0-f5ba-4c48-9283-983d02d88b32" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/98f31faf-cbbc-4aa0-a994-4bf2dd860e9b" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/13e72a1e-9b58-4daf-ab3a-d9d855cc75b6" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/bad65c7a-62e8-4a06-be8d-94ccbdfa4cc4" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/c1daf36b-8622-439a-8273-816b578668f7" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/e9c107f0-b17a-4cc0-bf51-e07e28f9bad3" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/315aa1c3-dfe2-49f1-88c5-1dbe7df53389" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/305d9e36-0693-4f61-ba59-cb5f96e9489b" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/3b2084b1-3d9f-4768-8f1a-bc6cc25c54e1" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/5cebc4ab-e3fe-46e8-a673-597640bff47f" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/de82192e-8951-4b39-a714-88ec7e1596d1" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/aec32548-3ba2-4a9e-a973-f23ed78d7f09" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/5a878ad7-9ed7-4d97-9a96-efdc934718af" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/f21a496a-818e-48cf-a98f-b896d7584bd7" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/0527174e-491e-44ca-b598-b963da6c0959" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/b93fd967-07fd-4ddd-8bdc-58dde9a8cd3e" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/707f9422-11c6-4332-a911-2f938ff56ca8" />

### 2. osTicket Installation & Configuration

- Installed osTicket and created the supporting MySQL database.
- Completed the guided osTicket setup, configuring database connectivity and required file permissions.
- Configured the initial osTicket environment and verified successful deployment by accessing the osTicket Staff Control Panel.

📌 Refer to the below screenshots: (left to right)

<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/c2dd0a06-0e1b-445f-9c33-617fd815844e" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/8e7753bc-5286-4e15-be7a-2ecd032566c3" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/2049340b-da21-4d5e-bdcb-1884f71c5580" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/c18f1627-8e69-480a-b883-7fc893a75ffb" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/76385713-b2b6-4f81-ad7f-ffd142d7f9c7" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/e22ccf37-7e0b-4ed7-839f-329556191b20" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/51338755-596b-467f-bcc2-fd4c91ac9794" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/97d30082-38da-457e-b0c8-f757be4dc9ab" />
<img width="260" height="230" alt="image" src="https://github.com/user-attachments/assets/c40a9b52-de53-4b57-a79e-b450f95a47d6" />
<img width="393" height="230" alt="image" src="https://github.com/user-attachments/assets/d039731c-366b-41c0-966b-af8e5ef4ee2b" />
<img width="393" height="230" alt="image" src="https://github.com/user-attachments/assets/aa998142-c5b0-4715-a2da-073bb2af93c0" />
<img width="393" height="230" alt="image" src="https://github.com/user-attachments/assets/21a99336-d47d-4cbb-b541-f34471952eb5" />
<img width="393" height="230" alt="image" src="https://github.com/user-attachments/assets/916d388d-ccf6-41fd-85db-f696f42a44e1" />



### 3. SIEM-to-Ticketing Integration
- Generated an API key within osTicket to authorize communication from the SIEM.
- Configured an Elastic connector using the osTicket API key to establish integration between Elastic and the ticketing platform.
- Built and configured a webhook connector to transmit alert information to osTicket in the required format.
- Generated a test SIEM alert and confirmed successful ticket creation and visibility within the osTicket Agent Panel.
- Validated the end-to-end workflow from SIEM detection through automated ticket creation.

📌 Refer to the below screenshots: (left to right)


### 4. Brute Force Investigation Methodology & Alert Routing
- Developed a structured investigation methodology for brute force alerts, focusing on:
  - Whether the source IP had a known malicious or suspicious history
  - Whether multiple user accounts were targeted
  - Whether any authentication attempts were successful
  - What activity occurred following successful authentication
  - Whether additional indicators suggested compromise or lateral movement
- Modified the Windows brute force detection rule to automatically route alerts into osTicket.
- Simulated brute force activity and verified that the resulting SIEM alert generated a corresponding investigation ticket.
- Applied IOC and IP reputation research to support alert validation and investigation.

📌 Refer to the below screenshots: (left to right)


### 5. SSH & C2 Detection Rule Alert Routing
- Configured the SSH brute force detection rule to automatically forward alerts into osTicket.
- Performed controlled SSH brute force simulations and verified successful alert-to-ticket generation.
- Configured the Mythic C2 detection rule to automatically route C2 alerts into osTicket.
- Validated the workflow through controlled C2 activity and confirmed that the resulting detection generated a trackable incident ticket.
- Applied timeline-building and event correlation techniques to support investigation of routed alerts.

📌 Refer to the below screenshots: (left to right)


### 6. Endpoint Detection & Response (EDR) Deployment & Validation
- Installed and configured Elastic EDR (Elastic Defend) on the Windows endpoint.
- Initiated a controlled malicious payload download attempt from the Mythic C2 infrastructure to validate endpoint protection.
- Confirmed that Elastic Defend successfully prevented the malicious payload download and generated a malware prevention alert.
- Verified that the blocked activity was visible and traceable within Elastic Discover.
- Configured an automated response action to isolate the endpoint following a Malware Prevention Alert.
- Repeated the controlled download attempt while monitoring endpoint connectivity through continuous ping testing.
- Confirmed that the prevention alert triggered the automated response and isolated the endpoint, resulting in loss of network connectivity.
- Validated the complete **detection → prevention → automated response → endpoint isolation** workflow.

📌 Refer to the below screenshots: (left to right)


