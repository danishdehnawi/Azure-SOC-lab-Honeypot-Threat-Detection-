 # Azure SOC Lab: Honeypot & Threat Detection

## Overview
This project demonstrates a real-world Security Operations Center (SOC) workflow built entirely in Microsoft Azure. A Windows 10 Virtual Machine was deliberately exposed to the public internet to function as a honeypot, attracting real-world attackers and capturing live brute-force and credential-stuffing activity. Microsoft Sentinel was used as the SIEM to ingest, analyze and visualize the attack data.

📊 Full Presentation: [Click Here](YOUR PRESENTATION LINK HERE)

---

## Objectives
- Deploy a vulnerable Windows 10 VM honeypot in Microsoft Azure
- Disable all firewall protections to maximize attack surface
- Capture real-world brute-force login attempts from malicious actors
- Forward Windows Security logs to Microsoft Sentinel via the Azure Monitoring Agent
- Write KQL queries to investigate and filter failed login attempts
- Configure automated Sentinel Analytics Rules to alert on suspicious IP activity
- Enrich log data with GeoIP information to map attack origins geographically
- Visualize global attack traffic using a live attack map in Microsoft Sentinel

---

## Tools & Technologies
- Microsoft Azure
- Windows 10 Virtual Machine
- Network Security Group (NSG)
- Log Analytics Workspace
- Microsoft Sentinel (SIEM)
- Azure Monitoring Agent (AMA)
- Kusto Query Language (KQL)
- Windows Event Viewer
- GeoIP Watchlist

---

## Lab Setup

### 1. Honeypot Infrastructure
- Provisioned a Windows 10 VM inside an Azure Resource Group and VNet
- Modified the Network Security Group to allow all inbound traffic
- Disabled Windows Defender Firewall across all profiles
- Confirmed public reachability via ICMP ping test

### 2. Log Collection & SIEM Integration
- Created a Log Analytics Workspace as the central log repository
- Integrated Microsoft Sentinel with the Log Analytics Workspace
- Installed the Azure Monitoring Agent on the VM to forward Windows Security logs to Sentinel
- Verified log ingestion via Event ID 4625 in Windows Event Viewer

### 3. Detection & Analysis
- Wrote KQL queries to filter failed login attempts by IP address
- Configured Sentinel Analytics Rule to alert when failed logins exceeded 30 per 5 minutes
- Uploaded GeoIP Watchlist to Sentinel to enrich logs with geographic data
- Built an attack map workbook to visualize global threat origins

---

## Key Findings
- The honeypot VM was discovered and targeted within minutes of deployment confirming how quickly automated bots identify exposed cloud infrastructure
- IP address 185.34.147.146 generated a high volume of failed login attempts using common default usernames including Administrator, User, Guest and Backup within a short time window
- Multiple IP addresses from different countries attacked the VM simultaneously confirming the global and automated nature of modern cyber threats
- The Sentinel Analytics Rule successfully triggered real-time alerts when failed logins exceeded 30 attempts within a 5 minute window
- The GeoIP enriched attack map revealed attack origins spanning multiple continents providing immediate geographic threat intelligence

---

## KQL Queries

### Query 1 — Failed Login Detection
```kql
SecurityEvent
| where EventID == 4625
| project TimeGenerated, Account, Computer, EventID, Activity, IpAddress

```



---

## Skills Demonstrated
- Microsoft Azure Administration
- Cloud Infrastructure Provisioning
- Network Security Group Configuration
- SIEM Deployment and Configuration
- Log Ingestion and Forwarding
- Kusto Query Language (KQL)
- Threat Detection and Analysis
- Security Alert Configuration
- GeoIP Log Enrichment
- Attack Visualization and Mapping
- Windows Event Log Analysis
- Incident Investigation

---

## Resources
- [GeoIP Watchlist](YOUR GITHUB RESOURCES FOLDER LINK HERE)
- [Attack Map JSON](YOUR GITHUB RESOURCES FOLDER LINK HERE)

