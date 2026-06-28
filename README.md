# Azure-SOC-lab-Honeypot-Threat-Detection-

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
- Azure
