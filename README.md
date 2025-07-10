# Active Directory 2.0 Cybersecurity Project

## Objective

The primary objective of this project was to establish a fully functional Active Directory (AD) environment in the cloud, implement Splunk for security monitoring and alerting to detect unauthorized logins, and integrate Shuffle as a Security Orchestration, Automation, and Response (SOAR) platform to automate incident response workflows. This comprehensive approach allows me to demonstrate my capabilities across multiple cybersecurity domains.

## Skills Learned

- Cloud Infrastructure Management (Vultr)
- Windows Server Administration (Active Directory, DNS)
- Linux Server Management (Ubuntu)
- Security Information and Event Management (SIEM) with Splunk (installation, configuration, data ingestion, alert creation for unauthorized RDP logins)
- Security Orchestration, Automation, and Response (SOAR) with Shuffle (workflow development, integration with Splunk, Slack, and Active Directory)
- Network Firewall Configuration (Vultr and host-based UFW)
- Troubleshooting and Problem Solving in complex environments

## Tools Used

- Vultr Cloud Platform
- Windows Server 2022
- Ubuntu 22.04
- Splunk Enterprise
- Shuffle SOAR Platform
- Slack for alert notifications
- draw.io for diagramming

## Steps

### Part 1: Diagramming the Environment

Before any build, I focused on visualizing my lab environment by creating a detailed diagram using draw.io. This crucial first step helped me map out the logical flow of my infrastructure and security components.

*Ref 1: Network Diagram*

![Network Diagram](https://imgur.com/your_image_url_here)

### Part 2: Cloud Infrastructure Setup

In this phase, I deployed and configured my three virtual machines in the Vultr cloud and ensured their network connectivity.

- Deployed VMs:
  - JAZEB-ADDC01: Windows Standard 2022 server with 2 vCPUs, 4GB RAM, and 80GB disk space.
  - Cloud instance: Windows Standard 2022 server with 1 vCPU, 2GB RAM, and 55GB disk space.
  - JAZEB-SPLUNK: Ubuntu 22.04 server with 4 vCPUs, 8GB RAM, and 160GB disk space.

- Firewall Configuration:
  - Created a Vultr firewall group (my-dfir-ad-project-2.0) to secure my VMs.
  - Restricted SSH (Port 22) and RDP (Port 3389) access to only my public IP address.

- Virtual Private Cloud (VPC) Network:
  - Enabled VPC for all three VMs, assigning them private IP addresses within the 10.22.96.x range.

### Part 3: Active Directory Configuration

This part involved transforming one of my Windows servers into a fully functional Domain Controller and integrating my test machine into the newly created domain.

- Domain Controller Setup:
  - Installed the Active Directory Domain Services role on JAZEB-ADDC01.
  - Promoted JAZEB-ADDC01 to a new forest with the domain name mydfir.local.

- User Creation:
  - Created a new user account: Jenny Smith (logon name JSmith, password Winter2025!).

- Domain Join:
  - Configured my Cloud instance to join the mydfir.local domain.
  - Resolved DNS resolution issues by configuring the Cloud instance's DNS server to point to JAZEB-ADDC01's private IP address.

### Part 4: Splunk Configuration and Alerting

This was a pivotal phase where I set up my Splunk environment to collect security telemetry and create an alert for unauthorized RDP logins.

- Splunk Server Installation:
  - Installed Splunk Enterprise on JAZEB-SPLUNK.
  - Configured Splunk's web interface and firewall settings.

- Windows Endpoint Telemetry Collection:
  - Installed the Splunk Universal Forwarder on both my Cloud instance and JAZEB-ADDC01.
  - Configured the Universal Forwarder to collect Windows Security Event Logs and send them to Splunk.

- Generating Test Data for Unauthorized Logins:
  - Simulated an external attack by performing an RDP login from a different external IP address.

- Creating an Alert for Unauthorized Successful RDP Logins:
  - Developed a Splunk Search Processing Language (SPL) query to identify unauthorized RDP logins.
  - Configured a scheduled alert to trigger if unauthorized RDP logins were detected.

### Part 5: Slack and Shuffle Automation

In the final part, I integrated Slack and Shuffle to automate the response to detected unauthorized logins, building a mini-playbook.

- Shuffle Setup:
  - Created an account on Shuffle and initiated a new workflow named my-dfir-ad-project-2.0.

- Splunk-Shuffle Webhook Integration:
  - Configured the Splunk alert to use a webhook action pointing to the Shuffle workflow.

- Slack Integration:
  - Created a Slack workspace (my-dfir-projects) and a dedicated channel named #alerts.
  - Configured the Shuffle workflow to send alert notifications to the #alerts channel.

- Email Notification for User Action:
  - Added a "User Input" node in Shuffle to send an email notification to a designated SOC analyst email address.

- Active Directory Integration for User Disablement:
  - Configured the "Active Directory" application within Shuffle to disable the user account if confirmed by the SOC analyst.

- Status Check and Final Slack Notification:
  - Implemented a mechanism to verify the user's disabled status before sending a final notification to the #alerts channel.

## Conclusion

This Active Directory 2.0 Cybersecurity Project has provided me with invaluable hands-on experience in building, securing, monitoring, and automating a critical enterprise environment. From designing the network architecture and configuring core services like Active Directory and Splunk, to developing advanced Splunk queries and orchestrating automated responses with Shuffle, I have gained a deep understanding of the practical aspects of security operations. This project specifically highlights my capabilities in various cybersecurity domains and demonstrates my readiness to contribute effectively as a SOC Analyst.
                                  
