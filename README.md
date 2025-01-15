<h1>AZURE HONEYPOT HOME LAB</h1>

<h2>Overview</h2>
<p>This project demonstrates the process of how I was able to create, log and visualize malicious attacks on a Windows Virtual Machine created in Microsoft Azure.
</p>

<p align="center">
<img height="85%" width="85%" alt="Attack-Map_1-3-2025" src="https://github.com/user-attachments/assets/d01b75b4-0bbb-417a-a516-1ed42fa3ed1c" />
</p>


<h2>Languages Used</h2>
- <b>PowerShell:</b> Extract RDP failed logon logs from Windows Event Viewer <br>
- <b>KQL:</b> Parse raw data fron extracted failed RDP logons

<h2>Utilities Used</h2>
- <b>ipgeolocation.io:</b> IP Address to Geolocation API
<br>
<br>
<br>


<h2>Project Walkthrough</h2>
<h3>Microsoft Azure: Creating a Virtual Machine</h3>
<p>Through Microsoft Azure I was able to quickly create and access machines that I can intentionally make susceptible to virtual attacks [i.e. a honeypot]. I created this virtual machine to run Windows 10, allow port 3389 access, and defaulted to all other minimal security settings available within this Azure account. </p>

<p align="center">
<img height="85%" width="85%" alt="Screenshot 2025-01-14 at 3 11 48 PM" src="https://github.com/user-attachments/assets/4e3a89d5-a5df-42fb-ab3a-1fc9c11f482c" />
</p>


<h3>Windows Virtual Machine: Inviting Vulnerabilities</h3>
<p>To ensure my virtual machine became a tempting target for malicious activity I remoted into my created virtual machine using RDP to disable the domain, public, and private firewalls within Windows Firewall with Advanced Security(wf.msc). <br><br>I signed out of my honeypot to test whether or not it was indeed logging suspicious activity. I then intentionally input incorrect credentials when remoting into my honeypot before then inserting correct ones. To confirm malicious activity I was able to locate information around my incorrect login within the Event Viewer <i>[Start Menu > Event Viewer > Windows Logs > Security]</i>.</p>


<h3>Powershell/Geolocation API: Log Collection</h3>
<p>To verify that </p>
<br>
<p align="center">
<img height="85%" width="85%" alt="Powershell-script-logs" src="https://github.com/user-attachments/assets/567ab051-ae85-4f49-9a0d-19af88050b20" />
</p>
<br>
<br>

<h2>World Map: After 24 hours</h2> <!-- (built custom logs including geodata)</h2> -->

<p align="center">
<img height="85%" width="85%" alt="24hour Attack-Map_1-3-2025" src="https://github.com/user-attachments/assets/e24f3b96-e373-45b4-9e76-435ab5bb672d" />
</p>
