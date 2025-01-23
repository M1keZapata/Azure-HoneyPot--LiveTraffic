# Azure SOC + Honeynet (Live Traffic)
</p>

<p align="center">
<img height="85%" width="100%" alt="Attack-Map_1-3-2025" src="https://github.com/user-attachments/assets/38b01efc-f837-498c-8f4c-b0128185c997" />
</p>

## Project Overview ##
<p>This project demonstrates the construction of a mini honeynet within the Azure platform. The objective was to capture and analyze logs from several sources, subsequently consolidated within a Log Analytics workspace. <br><br> 
Microsoft Sentinel was championed to leverage these logs to developing attack maps, create alert triggers, and incident generation. Expressed throughout this project are metrics of an insecure environment over a 24-hour period.


## Technologies, Azure Components, and Regulations Employed
- Azure Network Security Groups (NSG)
- Virtual Machine (2 Windows VMs)
- Log Analytics Workspace with Kusto Query Language (KQL) Queries
- Microsoft Sentinel for Security Information and Event Management (SIEM)
- Windows Remote Desktop for Remote Access
- Command Line Interface (CLI) for System Management
- PowerShell for Automation and Configuration Management
- [NIST SP 800-53 Revision 5](https://csrc.nist.gov/publications/detail/sp/800-53/rev-5/final) for Security Controls
- [NIST SP 800-61 Revision 2](https://www.nist.gov/privacy-framework/nist-sp-800-61) for Incident Handling Guidance

<br>
<br>



## Azure Architecture / Exposure
<p align="center">
<img height="85%" width="100%" alt="Screenshot 2025-01-14 at 3 11 48 PM" src="https://github.com/user-attachments/assets/4e3a89d5-a5df-42fb-ab3a-1fc9c11f482c" />
</p>
<p>Through Microsoft Azure I was able to quickly create and deploy virtual windows machines that I can expose to the public for malicious actors to discover [i.e. a honeypot]. These machines were configured to run Windows 10, and their network security groups (NSGs) had Allow All configured. To further entice attackers I RDP'd into each of my machines to disable the domain, public, and private firewalls within Windows Firewall with Advanced Security(wf.msc). </p>


<p>To confirm attack, I intentionally input incorrect credentials when remoting into my machines before then inserting correct ones. To confirm malicious activity I was able to locate logs around my failed login locally within the Event Viewer<i>[Start Menu > Event Viewer > Windows Logs > Security]</i>.</p>


### Powershell/Geolocation API: Log Collection
<p align="center">
<img height="85%" width="100%" alt="Powershell-script-logs" src="https://github.com/user-attachments/assets/567ab051-ae85-4f49-9a0d-19af88050b20" />
</p>

#### After diligently scouring Reddit, I was able to find an API that would embelish the following data from the attack logs: 
- Longitude
- Latitude
- Destination Host
- Username
- Source Host
- Country
- Timestamp

These key extractions proved useful when creating custom logs in Azure and parsing data through KQL queries. This way I was able to map the source of where attacks were coming from. This would later be instrumental in quickly communicating and tieing the project at large together to those interested in learning about it.


<br>
<br>


## Attack Maps Before Hardening 
<b>This attack map shows the traffic allowed by a Network Security Group with all traffic allowed inbound</b>
NSG Allowed Inbound Malicious Flows

<p align="center">
<img height="85%" width="100%" alt="24hour Attack-Map_1-3-2025" src="https://github.com/user-attachments/assets/e24f3b96-e373-45b4-9e76-435ab5bb672d" />
</p>

## Metrics Before Hardening / Security Controls
The following table shows the metrics measured within the unsecured environment for 24 hours:

| Metric                   | Count
| ------------------------ | -----
| SecurityEvent            | 16779
| Syslog                   | 190
| SecurityAlert            | 103
| SecurityIncident         | 102
| AzureNetworkAnalytics_CL | 528

## Conclusion

In this project, a mini, but effective, honeynet was constructed in Microsoft Azure, and log sources were integrated into a Log Analytics workspace. Microsoft Sentinel was configured to trigger alerts and create incidents based on the ingested logs. Additionally, metrics were measured in the unsecured environment before security controls were applied and after implementing security measures.
