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

### 1. Ticketing System Research & Web Server Environment Setup:

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

### 2. osTicket Installation & Configuration:

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

### 3. SIEM-to-Ticketing Integration:
- Generated an API key within osTicket to authorize communication from the SIEM.
- Configured an Elastic connector using the osTicket API key to establish integration between Elastic and the ticketing platform.
- Built and configured a webhook connector to transmit alert information to osTicket in the required format.
- Generated a test SIEM alert and confirmed successful ticket creation and visibility within the osTicket Agent Panel.
- Validated the end-to-end workflow from SIEM detection through automated ticket creation.

📌 Refer to the below screenshots: (left to right)

<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/e032a134-9812-4317-88b8-8ac289226c4b" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/3be6d8a4-edab-4b0f-9e47-ee7249220393" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/2226d13c-5c47-43b2-b431-a1f4a01475f3" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/bf3e6a9f-3c36-4c73-add1-723c9e5fa520" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/106eb86d-d16e-43a0-a83d-f04c1f4e07e8" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/cdb8483c-2587-47f5-8bdc-5726b44efa03" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/768dde8b-c529-476c-a94f-2ec67f10bdd6" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/40dceec1-5c4b-41cc-97d2-51d8b30f4bf2" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/5abcdbd0-e856-47a1-a75f-d6ab71b35fc8" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/0bb7fefd-89e6-475e-acfc-4269b6363a2d" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/5a703dcb-2a45-470a-aeeb-1bfa2e1dbb36" />
<img width="975" height="563" alt="image" src="https://github.com/user-attachments/assets/d7675d02-08cf-4dc4-a463-8a5758dd115c" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/9d597680-b785-4518-b435-9d78c6a10dc8" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/ee0cc608-2a2b-4307-adb9-bc26f16583d5" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/cd007896-0a47-4fa2-997f-6436c0304834" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/0f9d928f-2028-45cb-8aad-464d2b2d92eb" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/0ede8908-394e-4021-9d3d-ea1835cd8a32" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/24ee28c1-f8e3-4ede-91a8-1314d79b29d5" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/9df80b8e-49c2-4b96-b039-74b2a3052a65" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/0447be6f-b12c-4828-9f86-5c48c6c82d10" />

### 4. Brute Force Investigation Methodology & Alert Routing:
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

<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/43327c82-7fa1-46c3-9cf1-fd263d1d920b" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/8321a279-5a67-4edf-a011-cb5896efb317" />
<img width="975" height="556" alt="image" src="https://github.com/user-attachments/assets/a63781ec-6cc4-48d3-83ac-3609e9742ebb" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/73db7672-a857-4225-9b89-544696b86f16" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/8682a567-3e85-4179-8bcb-83ce152a5782" />
<img width="975" height="557" alt="image" src="https://github.com/user-attachments/assets/da98d546-b428-4b9f-b3c0-3f0df272f3a9" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/e5aa7d1f-ecb3-4c63-8273-d4d9ef849b75" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/813ce5e7-3d29-4b9f-ab18-35e5447c37df" />

### 5. SSH & C2 Detection Rule Alert Routing:
- Configured the SSH brute force detection rule to automatically forward alerts into osTicket.
- Performed controlled SSH brute force simulations and verified successful alert-to-ticket generation.
- Configured the Mythic C2 detection rule to automatically route C2 alerts into osTicket.
- Validated the workflow through controlled C2 activity and confirmed that the resulting detection generated a trackable incident ticket.
- Applied timeline-building and event correlation techniques to support investigation of routed alerts.

📌 Refer to the below screenshots: (left to right)

<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/ef865f30-3145-4f15-878a-583c62c5cc8e" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/49422d92-4c47-433f-ba77-5fc25418555e" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/1514cbe9-b349-4a44-9b23-5cc18d414208" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/adec9608-c1dd-4892-ab2c-d5520e0ee802" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/f4ead941-57e4-4ffb-9722-b11f9a823480" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/a899f38d-dd00-4193-b84a-830899096057" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/5f51d193-3584-4073-a80d-783636917acd" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/84d99784-6352-4954-b139-53c5eae6ed1e" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/6aaffbfb-5ffe-4737-910c-d74272e07d1c" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/1fb93ace-9397-46ba-b0f3-b600631e99f2" />
<img width="975" height="562" alt="image" src="https://github.com/user-attachments/assets/cefc66ae-52cb-4a81-a186-97864d32d764" />

### 6. EDR Deployment & Malware Prevention Validation:

- Installed and configured Elastic EDR (Elastic Defend) on the Windows endpoint.
- Initiated a controlled malicious payload download attempt from the Mythic C2 infrastructure to validate endpoint protection.
- Confirmed that Elastic Defend successfully prevented the malicious payload download and generated a malware prevention alert.
- Verified that the blocked activity and associated prevention alert were visible and traceable within Elastic Discover.

📌 Refer to the below screenshots: (left to right)



### 7. Automated Response Action Setup & Testing:

- Configured an automated response action to isolate the endpoint when a Malware Prevention Alert was generated.
- Repeated the controlled malicious payload download attempt to trigger the configured response action.
- Monitored endpoint connectivity through continuous ping testing during the validation.
- Confirmed that the prevention alert triggered the automated response and successfully isolated the endpoint, resulting in loss of network connectivity.
- Validated the complete **detection → prevention → automated response → endpoint isolation** workflow.

📌 Refer to the below screenshots: (left to right)

<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/c7f99432-b700-47a4-a5ae-537e30239f37" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/4ea0ae4d-ac8b-4078-9451-a0fa14518fad" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/f8894f2e-a899-4914-b356-55d16e93e240" />
<img width="975" height="559" alt="image" src="https://github.com/user-attachments/assets/03485cad-d70e-4e51-9672-a71a97cb6c66" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/345fe0bc-3744-4d53-a886-7550a403afbf" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/c40a9ee0-9365-4b32-8c8a-7734b2ba81dc" />
<img width="975" height="558" alt="image" src="https://github.com/user-attachments/assets/a76c6b8d-8250-452d-85a4-346fa7c7e2fd" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/b61d9fdd-8536-4cfc-8de9-ef30c1b64324" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/23aeed32-6824-40ee-82f4-635ca751a54d" />
<img width="975" height="561" alt="image" src="https://github.com/user-attachments/assets/adc5fb05-4238-4e80-896e-847198f38c45" />
<img width="975" height="550" alt="image" src="https://github.com/user-attachments/assets/6b83e407-455e-4b0a-a3cd-9bde5cf629e7" />
<img width="975" height="581" alt="image" src="https://github.com/user-attachments/assets/6ac74e96-e845-48f7-b543-71802f76d033" />
<img width="975" height="581" alt="image" src="https://github.com/user-attachments/assets/ff6b6468-8466-47c6-9ffd-5639f9b38a76" />
<img width="975" height="582" alt="image" src="https://github.com/user-attachments/assets/86395ccd-4394-4a8c-9efc-30f8c5233c1b" />
<img width="975" height="560" alt="image" src="https://github.com/user-attachments/assets/9c0612d2-c5f8-427e-be8e-c3ebf469a72b" />



