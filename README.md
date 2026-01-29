# Azure Sentinel SIEM Honeypot Lab

## 📌 Overview
This project focuses on building a **cloud-native SIEM honeypot** using **Microsoft Azure Sentinel** to observe and analyze real-world brute-force activity. A deliberately exposed Windows endpoint was deployed to attract malicious traffic, enabling hands-on experience with log ingestion, enrichment, KQL analytics, and global attack visualization.

---

## 🎯 Project Objective
The primary goal was to design and implement a **high-visibility Azure Sentinel SIEM lab** that captures live attack telemetry, enriches raw security logs with contextual data, and visualizes attacker behavior across different geographies. This project bridges theoretical SOC concepts with practical, real-world implementation.

<img width="1442" height="756" alt="image" src="https://github.com/user-attachments/assets/0c8259ef-3b2b-48fd-9d64-c602a4cab1e0" />

---

## 🧠 Skills Gained
- Microsoft Sentinel SIEM configuration and monitoring  
- Kusto Query Language (KQL) for security analytics  
- PowerShell scripting for log extraction and enrichment  
- Azure Network Security Group (NSG) and firewall configuration  
- Analysis of brute-force and credential-stuffing attack patterns  

---

## 🛠️ Tools & Technologies
- **Microsoft Sentinel** – Centralized SIEM and threat visualization  
- **Microsoft Azure** – Cloud infrastructure and VM hosting  
- **PowerShell** – Log processing and API-based enrichment  
- **Geolocation API** – IP-based location enrichment  
- **Kusto Query Language (KQL)** – Log parsing and analytics  

---

## 🧪 Project Implementation

### Phase 0: Environment Provisioning
To establish the lab foundation, Azure resources were provisioned to support centralized logging and attack monitoring:
- Deployed a **Windows 11 Pro virtual machine** as a high-exposure target system.
<img width="1385" height="468" alt="image" src="https://github.com/user-attachments/assets/8a1a223b-a3db-4931-b653-eb08b8f44ab4" />

- Created a dedicated **Log Analytics Workspace (LAW)** to retain telemetry independently of the endpoint state.
<img width="1904" height="397" alt="image" src="https://github.com/user-attachments/assets/2306e84f-ce33-440d-8f04-35be4d959752" />

- Configured Azure Resource Groups and Virtual Network components.
<img width="1909" height="400" alt="image" src="https://github.com/user-attachments/assets/436c4a7e-891e-4679-b6b4-09f2cceaacca" />

---

### Phase 1: Attack Surface Configuration
To ensure sufficient attack telemetry, the security posture of the VM was intentionally weakened:
- Configured **Network Security Group (NSG)** rules to allow unrestricted inbound traffic.
<img width="1386" height="847" alt="image" src="https://github.com/user-attachments/assets/988156f5-f735-43e5-a750-d2605ea6c8fe" />

  
- This controlled exposure was used strictly for lab purposes to attract automated scanners and botnet activity.

---

### Phase 2: Telemetry Engineering & Log Enrichment
Raw Windows security events were transformed into context-rich security data:
- Extracted failed authentication events (Event ID 4625) using **PowerShell**.
- Enriched logs with **geolocation data** (latitude, longitude, country) via an external API.
- Stored enriched output in a custom log file for SIEM ingestion.
- Parsed and structured data using custom **KQL queries**.
<img width="1636" height="846" alt="image" src="https://github.com/user-attachments/assets/bc90a2e3-fea4-48d7-b083-2c9f67c6a729" />

- - Run below KQL query in Sentinel:
<img width="1634" height="808" alt="image" src="https://github.com/user-attachments/assets/e3c141a8-bca8-40e2-980e-6025266d4850" />
-  If you see Event IDs like 4624 and 4625, you're connected.

---

### Phase 3: SIEM Integration & Analytics
- Configured **Data Collection Rules (DCRs)** to ingest custom logs into Microsoft Sentinel.
<img width="1807" height="352" alt="image" src="https://github.com/user-attachments/assets/d8eaca2f-4f14-4a9e-a822-b60a476bbe98" />


- Developed KQL queries to aggregate attack data by source location.
- Created **watchlists** and built an interactive **attack map workbook** for visualization.
<img width="1617" height="607" alt="image" src="https://github.com/user-attachments/assets/ea6e7ad7-e56c-4a43-8311-93e3f60799bf" />

**attack map workbook**
<img width="1629" height="454" alt="image" src="https://github.com/user-attachments/assets/dac7b553-4bf0-4a1f-b797-139fed0b7250" />

---

### Phase 4: Detection Engineering
To operationalize the lab:
- Designed an **anomaly-based analytics rule** in Sentinel.
<img width="1591" height="716" alt="image" src="https://github.com/user-attachments/assets/a63a4a07-087d-498a-a2c5-b853b331246c" />

- Enabled alerting on abnormal authentication patterns indicative of brute-force behavior.
<img width="1912" height="681" alt="image" src="https://github.com/user-attachments/assets/e52d1e3b-2346-4de2-83a2-70fd4ac5223a" />


---

## 🌍 Observations & Findings
- The exposed VM began receiving attack traffic **within minutes** of firewall rule changes.
- A significant concentration of brute-force attempts originated from **Jordanów (Poland)**, followed by regions in the **Netherlands** and **Prague**.

- 
  **Attack map**
  <img width="1118" height="601" alt="image" src="https://github.com/user-attachments/assets/f1bc03ac-4c62-47e5-a515-e1733937f3de" />

- Repeated credential-stuffing attempts targeted default administrative accounts, highlighting common attacker automation techniques in cloud environments.

---

## 📊 Final Outcome
This project delivered practical experience in **cloud-native SIEM engineering**, end-to-end log pipelines, and real-time threat visualization. It reinforced how raw security telemetry can be transformed into actionable intelligence through enrichment, analytics, and detection logic.
