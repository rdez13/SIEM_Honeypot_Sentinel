## SIEM Honeypot Sentinel

## Overview

The Azure Sentinel RDP Honeypot project demonstrates how to create a honeypot environment using Azure Sentinel to attract and monitor attackers. By deploying a Windows virtual machine (VM) with an intentionally disabled firewall, we can lure malicious actors and capture RDP (Remote Desktop Protocol) activity. Attack data is collected through PowerShell scripts and visualized using Azure Sentinel for global insights.

## Project Details

This setup involves a PowerShell script that parses failed RDP login attempts from the Windows Event Logs. Additionally, a third-party API, ipgeolocation.io, is used to retrieve geolocation information, enabling us to pinpoint the physical location of potential attackers.

The following steps outline the workflow:

1. **VM Deployment and RDP Configuration:**

   - A Windows VM is created to simulate an environment vulnerable to RDP attacks.
   - Failed RDP login attempts are tracked and logged using the Windows Event Viewer.

2. **PowerShell Script for Log Parsing:**

   - A custom PowerShell script collects failed RDP login attempts.
   - The script integrates with the ipgeolocation.io API to add geolocation data to each log entry, revealing the source of attacks.

3. **Connecting to Log Analytics:**

   - The VM is linked to Azure Log Analytics for further analysis, using KQL (Kusto Query Language) to query the captured RDP log data.

4. **Visualizing Attacks in Azure Sentinel:**

   - The enriched RDP log data is displayed in an Azure Sentinel workbook, offering a global perspective of attack attempts.
   - Visualizations include graphs that display the frequency of attacks and their geographical distribution.

## Key Features

- **RDP Attack Logs with Geolocation:** Failed RDP login attempts are logged from the Windows Event Viewer and enriched with geographic information from the ipgeolocation.io API.
- **Live Attack Monitoring:** Azure Sentinel captures and visualizes brute-force RDP attacks in real time from the honeypot VM.
- **Custom PowerShell Script:** The project includes a custom PowerShell script that enhances RDP logs with attacker location details.
- **Log Analytics Support:** The project integrates with Azure Log Analytics, utilizing KQL to analyze and query raw RDP logs.
- **Azure Sentinel Workbook:** A detailed workbook in Azure Sentinel provides visualization of attack data, showing both frequency and the global origin of the attacks.

## Languages Used
**PowerShell:** Used to extract and enhance data from failed RDP login attempts.
![log_exporter_scrn](https://github.com/rdez13/SIEM_Honeypot_Sentinel/blob/4b121428bba09dd6c27211ad846c9e5041dc7f92/log_exporter_scrn.png)

## Tools and APIs Used
**ipgeolocation.io:** Provides IP geolocation services, converting IP addresses into location data to identify where attacks are coming from.

## Attack Visualization Flow
After 2 days, the logs are processed and displayed on a world map, giving a comprehensive view of the attackers’ geographical locations.
![Failed_RDP_Map](https://github.com/rdez13/SIEM_Honeypot_Sentinel/blob/4b121428bba09dd6c27211ad846c9e5041dc7f92/Failed_RDP_Map.png)
