# Azure Sentinel SIEM Honeypot Lab

## 📌 Overview
This project focuses on building a **cloud-native SIEM honeypot** using **Microsoft Azure Sentinel** to observe and analyze real-world brute-force activity. A deliberately exposed Windows endpoint was deployed to attract malicious traffic, enabling hands-on experience with log ingestion, enrichment, KQL analytics, and global attack visualization.

---

## 🎯 Project Objective
The primary goal was to design and implement a **high-visibility Azure Sentinel SIEM lab** that captures live attack telemetry, enriches raw security logs with contextual data, and visualizes attacker behavior across different geographies. This project bridges theoretical SOC concepts with practical, real-world implementation.


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
- Deployed a **Windows 10 Pro virtual machine** as a high-exposure target system.
- Created a dedicated **Log Analytics Workspace (LAW)** to retain telemetry independently of the endpoint state.
- Configured Azure Resource Groups and Virtual Network components.

<img width="1385" height="468" alt="image" src="https://github.com/user-attachments/assets/0208e7a1-3726-41a7-b5b8-e594d9101e2e" />


---

### Phase 1: Attack Surface Configuration
To ensure sufficient attack telemetry, the security posture of the VM was intentionally weakened:
- Configured **Network Security Group (NSG)** rules to allow unrestricted inbound traffic.
- This controlled exposure was used strictly for lab purposes to attract automated scanners and botnet activity.

---

### Phase 2: Telemetry Engineering & Log Enrichment
Raw Windows security events were transformed into context-rich security data:
- Extracted failed authentication events (Event ID 4625) using **PowerShell**.
- Enriched logs with **geolocation data** (latitude, longitude, country) via an external API.
- Stored enriched output in a custom log file for SIEM ingestion.
- Parsed and structured data using custom **KQL queries**.

---

### Phase 3: SIEM Integration & Analytics
- Configured **Data Collection Rules (DCRs)** to ingest custom logs into Microsoft Sentinel.
- Developed KQL queries to aggregate attack data by source location.
- Created **watchlists** and built an interactive **attack map workbook** for visualization.

---

### Phase 4: Detection Engineering
To operationalize the lab:
- Designed an **anomaly-based analytics rule** in Sentinel.
- Enabled alerting on abnormal authentication patterns indicative of brute-force behavior.

---

## 🌍 Observations & Findings
- The exposed VM began receiving attack traffic **within minutes** of firewall rule changes.
- A significant concentration of brute-force attempts originated from **Jordanów (Poland)**, followed by regions in the **Netherlands** and **Argentina**.
- Repeated credential-stuffing attempts targeted default administrative accounts, highlighting common attacker automation techniques in cloud environments.

---

## 📊 Final Outcome
This project delivered practical experience in **cloud-native SIEM engineering**, end-to-end log pipelines, and real-time threat visualization. It reinforced how raw security telemetry can be transformed into actionable intelligence through enrichment, analytics, and detection logic.
