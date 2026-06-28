# Azure SOC Lab: Honeypot & Threat Detection


## Project Documentation / Presentation

The full presentation and documentation for this lab can be accessed here:

[Azure SOC Lab Presentation](https://gmuedu-my.sharepoint.com/:p:/g/personal/ddehnawi_gmu_edu/IQDX5zp-NKSfQJxkTDSWxc0IAXEMLbqllncyqLni81Sp7wQ?e=zlx87S)

---


## Overview

This project demonstrates a real-world Security Operations Center (SOC) workflow built entirely in Microsoft Azure. A Windows 10 Virtual Machine was intentionally exposed to the public internet to function as a honeypot, attracting real-world attackers and capturing live brute-force and credential-stuffing activity. Microsoft Sentinel was used as the SIEM to collect, analyze, and visualize attack data.

---

## Objectives

- Deploy a vulnerable Windows 10 VM honeypot in Microsoft Azure
- Disable Windows Defender Firewall to maximize the attack surface
- Capture real-world brute-force login attempts from malicious actors
- Forward Windows Security logs to Microsoft Sentinel using the Azure Monitoring Agent (AMA)
- Write KQL queries to investigate failed login attempts
- Configure Microsoft Sentinel Analytics Rules for automated alerting
- Enrich logs with GeoIP data
- Visualize global attack activity using an Attack Map

---

## Tools & Technologies

- Microsoft Azure
- Windows 10 Virtual Machine
- Azure Resource Group
- Virtual Network (VNet)
- Network Security Group (NSG)
- Log Analytics Workspace
- Microsoft Sentinel (SIEM)
- Azure Monitoring Agent (AMA)
- Kusto Query Language (KQL)
- Windows Event Viewer
- GeoIP Watchlist

---

# Lab Setup

## 1. Honeypot Infrastructure

- Created an Azure Resource Group
- Deployed a Windows 10 Virtual Machine
- Created a Virtual Network (VNet)
- Configured the Network Security Group (NSG) to allow all inbound traffic
- Disabled Windows Defender Firewall
- Verified the VM was publicly reachable

---

## 2. Log Collection & SIEM Integration

- Created a Log Analytics Workspace
- Connected Microsoft Sentinel to the workspace
- Installed the Azure Monitoring Agent (AMA)
- Forwarded Windows Security Events to Sentinel
- Verified Event ID **4625** (Failed Logon) ingestion

---

## 3. Threat Detection & Analysis

- Created KQL queries to identify failed login attempts
- Configured an Analytics Rule to generate alerts after **30 failed logins within 5 minutes**
- Imported a GeoIP Watchlist
- Built an Attack Map Workbook to visualize attack origins

---

# Key Findings

- The honeypot was discovered within minutes of deployment.
- Automated bots immediately began brute-force login attempts.
- IP address **185.34.147.146** generated numerous failed logins using common usernames including **Administrator**, **User**, **Guest**, and **Backup**.
- Multiple IP addresses from different countries targeted the VM simultaneously.
- Microsoft Sentinel successfully generated alerts based on the Analytics Rule.
- GeoIP enrichment provided a visualization of attacker locations across multiple continents.

---

# KQL Query

## Failed Login Detection

```kql
SecurityEvent
| where EventID == 4625
| project TimeGenerated, Account, Computer, EventID, Activity, IpAddress
```

---

# Skills Demonstrated

- Microsoft Azure Administration
- Cloud Infrastructure Deployment
- Virtual Network Configuration
- Network Security Group (NSG) Management
- Windows Security Monitoring
- Log Analytics Workspace
- Microsoft Sentinel (SIEM)
- Azure Monitoring Agent
- Kusto Query Language (KQL)
- Threat Detection
- Security Alerting
- GeoIP Log Enrichment
- Attack Visualization
- Incident Investigation

---

## Resources

- **[GeoIP Watchlist](https://github.com/danishdehnawi/Azure-SOC-lab-Honeypot-Threat-Detection-/tree/main/Resources)**

- **[Attack Map JSON](https://github.com/danishdehnawi/Azure-SOC-lab-Honeypot-Threat-Detection-/tree/main/Resources)**

---

# Repository Structure

```text
Azure-SOC-lab-Honeypot-Threat-Detection-
│
├── Resources/
│   ├── GeoIP/
│   └── Map/
├── README.md
```
