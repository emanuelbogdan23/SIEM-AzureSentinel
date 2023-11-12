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


<h3>Setting up Azure Virtual Machine (VM)</h3>
<p>Using Azure Portal,  I began the process of creating a virtual machine (VM). This VM is intended to function as a honeypot, essentially a decoy exposed to the internet for simulated cyber attacks. I selected a resource group name, opting for 'honeypot-lab,' and named my virtual machine 'honeypot-vm.' For the VM's location, I chose the East US 2 region. The image and size settings were left at their default values. When prompted, I set a username and password for VM access, making sure to remember these credentials for later use.</p>
<br />
 <div align="center">
    <img src="https://imgur.com/jQk4KWI.png" height="90%" width="90%" alt="Azure VM Set Up"/>
  </div>
<br />

<h3>Setting up Log Analytics Workspace</h3>
<p>Continuing with the Azure setup, the next step was to configure a Log Analytics Workspace. I used the Log Analytics Workspace section to ingest logs from the virtual machine, specifically focusing on collecting Windows event logs. The primary purpose of this workspace is to facilitate the storage and analysis of logs, including the creation of a custom log containing geographic information. This customization is crucial for tracking and identifying the origins of potential attackers.

Creating the Log Analytics Workspace involved defining a space where these logs would be stored and processed. By ingesting Windows event logs and generating our custom log with geographic details, the workspace became a centralized hub for monitoring and analyzing the activities on the virtual machine.</p>


<h3>Setting up Azure Sentinel</h3>
<p>I proceeded to configure Azure Sentinel, our simulation tool for visualizing attack data. Azure Sentinel serves as a comprehensive security information and event management (SIEM) solution, offering a centralized platform for monitoring and responding to security threats. By connecting it to the Log Analytics Workspace, which aggregates logs from the virtual machine, including Windows event logs and custom logs with geographic information, Azure Sentinel enables us to analyze and visualize potential attacks in real-time. </p>

<h3>Powershell Script to Obtain Geo Data from Attackers</h3>
<p>The next step involved running a script continuously to extract geographic data from potential attackers. This script operated in perpetuity, continuously scanning the security event log for failed login attempts (Event ID 4625). When it detected such events, it captured the IP address, queried a geo-data API, and generated a log file. This log file, located in the C:\ProgramData folder (which is hidden), contained both sample records for training and real failed login attempts.

To set up the script, I obtained an API key for the geo-data API and pasted it into the script. The script ran continuously, monitoring the event viewer for failed logins and updating the log file with relevant information. This script allowed us to gather valuable data on potential attackers, including their geographical location.

The script seamlessly captured these events, providing latitude, longitude, and other details from the geo-data API. This ongoing process would intensify as more people discovered the virtual machine and attempted to log in.</p>
<br />
 <div align="center">
    <img src="https://imgur.com/ODD9lQd.png" height="90%" width="90%" alt="Azure VM Set Up"/>
  </div>
<br />


<h3>Integration of Geospatial Data - Custom Log in Log Analytics Workspace</h3>
<p>In the next step of the simulation, I established a custom log in the Log Analytics Workspace to integrate geospatial data from the virtual machine. This custom log enables us to centralize and analyze information from failed login attempts and their associated geographic details. In Azure, I selected "Custom logs" within the Log Analytics Workspace, creating a pathway to bring in the log file from the virtual machine.

Since the log file resides on the virtual machine, I copied its contents to my local machine, created a new log file, and saved it on my desktop. Back in Azure, I configured the custom log by specifying the collection path on the virtual machine, initiating the process to integrate this data into the Log Analytics Workspace. While the custom log is created immediately, it takes some time for synchronization between Log Analytics and the virtual machine.

This custom log setup enhances our analytical capabilities, contributing to a more comprehensive understanding of potential threats in our simulated environment.
</p>
<br />
 <div align="center">
    <img src="https://imgur.com/90Ftl6X.png" height="90%" width="90%" alt="Azure VM Set Up"/>
  </div>
<br />


<h3>Integration of Geospatial Data - Custom Log in Log Analytics Workspace</h3>
<p>In the final step, the deployment of Azure Sentinel played a pivotal role in visualizing and comprehending the extensive attack data generated throughout the project. Azure Sentinel served as the Security Information and Event Management (SIEM) tool, offering a high-level overview of the global attack landscape. By connecting Azure Sentinel to the previously established Log Analytics Workspace, the platform aggregated and processed the influx of log data, facilitating a comprehensive understanding of the threat landscape. The findings were striking, with over 15,000 login attempts originating from various countries within a span of approximately 6 hours. Noteworthy contributors included Netherlands, Bulguria, South Korea, and the United States. The attacks predominantly targeted the Remote Desktop Protocol (RDP), emphasizing the importance of securing such entry points. This conclusive phase underscored the significance of a robust SIEM solution in distilling actionable insights from voluminous log data, ultimately enhancing the cybersecurity posture of the virtual environment.
</p>
<br />
 <div align="center">
    <img src="https://imgur.com/dn1QdSp.png" height="90%" width="90%" alt="Azure VM Set Up"/>
  </div>
<br />

<h3>Key Learnings</h3>
<ol>
  <li><strong>Global Cyber Threat Landscape:</strong> The project vividly illustrated the global nature of cyber threats. The intentionally exposed virtual machine attracted attackers from diverse geographic locations, emphasizing the universal and persistent nature of cyber threats.</li>
  <li><strong>Targeted Attack Vectors:</strong>The concentration of attacks on the Remote Desktop Protocol (RDP) highlighted the importance of securing specific entry points. Cyber adversaries often focus on exploiting vulnerabilities in widely used services, making it crucial to fortify and monitor such access points.</li>
  <li><strong>Geospatial Data Insights:</strong> Extracting and enriching IP address data using PowerShell and integrating geospatial information into the Log Analytics Workspace enhanced the depth of threat analysis. Geographical insights into attack origins proved valuable for understanding the distribution and intensity of cyber threats.</li>
  <li><strong>SIEM's Analytical Power:</strong> Azure Sentinel demonstrated its effectiveness as a Security Information and Event Management (SIEM) solution. By aggregating and visualizing log data, it provided a comprehensive overview of the attack landscape, showcasing the value of SIEM in monitoring and responding to security threats.</li>
</ol>
<br />















