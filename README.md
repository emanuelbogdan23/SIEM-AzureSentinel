<h1>SIEM - Azure Sentinel</h1>

<h2>Description</h2>
In this SIEM project, I'll set up a free Azure subscription and then create a virtual machine with intentionally turned off firewalls to make it a tempting target for attackers. We will also manage logs in Azure's Log Analytics Workspace and use Azure Sentinel, Microsoft's SIEM, to map out attacker data. Additionally, I'll use PowerShell to extract and enrich IP address data for a deeper dive into cybersecurity threats.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b>
- <b>Microsoft Azure</b> 
- <b>Azure Sentinel (SIEM)</b> 
- <b>Log Analytics Workspace</b>

<h2>Project walk-through:</h2>

<p>
The diagram below illustrates our lab where an intentionally exposed virtual machine attracts global attackers. Leveraging the Log Analytics Workspace and PowerShell, we'll transform the generated logs created by failed RDP attempts. The next step involves utilizing Microsoft Sentinel (SIEM) to harness this log data, creating a comprehensive map that traces the origins of attacks through the corresponding attacking IP addresses. This process allows us to gain valuable insights into the diverse sources of potential security threats and view the attacks in a visually appealing way.
<br/>
<br />
<img src="https://imgur.com/beoyvSa.png" height="90%" width="90%" alt="High Level Overview"/>
<br />
<br />






