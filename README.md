# splunk-windows-eventlog-homelab
Splunk Enterprise home lab focused on Windows log ingestion, forwarder configuration, SPL searches, and security event analysis.

The objective of this lab was to gain hands-on experience with log collection, forwarding, indexing, searching, and troubleshooting within Splunk. A Windows 11 virtual machine was configured to forward Security, System, and Application logs to Splunk Enterprise using the Splunk Universal Forwarder.

Technologies Used
- Splunk Enterprise
- Splunk Universal Forwarder
- Docker
- Windows 11 Virtual Machine
- SPL (Search Processing Language)
- Windows Event Logs
- Lab Architecture

  
Windows 11 VM
      │
      │ Universal Forwarder
      ▼
Splunk Enterprise
(Docker Container)
      │
      ▼
homelab Index


Project Objectives
- Deploy Splunk Enterprise using Docker
- Create and manage custom indexes
- Configure Splunk Universal Forwarder
- Collect Windows Security, System, and Application logs
- Practice SPL searches and log analysis
- Troubleshoot network connectivity and forwarding issues
- Build foundational SIEM monitoring skills
- Configuration


Windows Event Log Inputs
[WinEventLog://Security]
disabled = 0
index = homelab

[WinEventLog://System]
disabled = 0
index = homelab

[WinEventLog://Application]
disabled = 0
index = homelab
Forwarding Configuration
[tcpout]
defaultGroup = default-autolb-group

[tcpout:default-autolb-group]
server = <splunk-server-ip>:9997

[tcpout-server://<splunk-server-ip>:9997]

SPL Searches Practiced

- View All Events
index=homelab
Count Events by Sourcetype
index=homelab
| stats count by sourcetype

- Top Event Codes
index=homelab
| stats count by EventCode
| sort -count

- Successful Logons
index=homelab EventCode=4624
Failed Logons
index=homelab EventCode=4625

- Events by Host
index=homelab
| stats count by host

Skills Demonstrated
- Splunk Enterprise Administration
- Docker Container Management
- - Windows Event Log Collection
- Splunk Universal Forwarder Configuration
- Log Ingestion and Indexing
- SPL Query Development
- Network Troubleshooting
- SIEM Fundamentals
- Security Event Analysis
- Challenges and Troubleshooting

Throughout the project, several issues were identified and resolved, including:

- Windows VM network connectivity issues
- VPN-related communication problems
- Incorrect forwarding destination IP addresses
- Universal Forwarder configuration errors
- Port connectivity validation using PowerShell
- Verification of log ingestion into Splunk

Resolving these issues provided valuable experience in diagnosing and troubleshooting real-world logging and monitoring environments.

Results

Successfully deployed Splunk Enterprise in Docker and configured a Windows 11 endpoint to forward Security, System, and Application logs into a custom Splunk index.

Verified successful ingestion of Windows Event Logs and performed SPL searches to analyze event activity.

Future Enhancements
- Create a Windows Security Monitoring Dashboard
- Build visualizations for authentication activity
- Simulate security events for detection testing
- Add Windows Server as an additional log source
- Develop custom SPL detections and alerts
- Expand into SOC-style monitoring scenarios


Anthony Gomes

CompTIA Security+ | Network Systems Technology (Enterprise & Cloud) | Home Lab Enthusiast

Building hands-on cybersecurity, systems administration, and security monitoring experience through practical projects and continuous learning.
