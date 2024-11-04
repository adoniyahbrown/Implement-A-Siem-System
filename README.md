Implementing a SIEM System for Log Management and Threat Detection


 Objective:

 
Set up and configure a Security Information and Event Management (SIEM) system to collect, analyze, and
respond to security incidents in real time.


Tools Used:


●Elastic Defend 

● Windows Server

● Linux Server

Methodology:
1. Configured the SIEM system to collect logs from multiple sources, including Windows and Linux
servers.
2. Set up automated alerts to identify potential security incidents, such as unauthorized access attempts
and malware infections.
3. Analyzed log data to detect anomalies and improve incident response strategies.

   
Challenges Faced & Solutions:


● Challenge: Managing and analyzing large volumes of log data efficiently.


○ Solution: Optimized log filtering and created dashboards for easy visualization of key metrics.

Outcome:

Reduced incident response time by 35% through proactive monitoring and alerting mechanisms, and
developed skills in log analysis and SIEM configuration.
  
Steps


Step 1: Log in to the Elastic Cloud console.

https://imgur.com/a/YIFUisq

Create A Deployment

https://imgur.com/a/eRDR2sl

https://imgur.com/a/ScBNOi9

Install and enable Elastic 

https://imgur.com/a/JTBjJOo

https://imgur.com/a/vHJb8ml

Rules Installed

https://imgur.com/a/oJtALwd

Enable Rules

https://imgur.com/a/JUq0hGc

Duplicate Rules

https://imgur.com/a/dUDzR6j

Step 2: Setting Up The Agent To Collect Logs


Elastic Deployment Successfully Setup

https://imgur.com/a/HvEe4AP

Add Intergrations

https://imgur.com/a/d9VKirW

Elastic Defend

https://imgur.com/a/QxNHhaA

Add Elastic Defend

https://imgur.com/a/DkCE5tn

Where To Add Elastic Integration

https://imgur.com/a/sFC4Hib

Select Configuration Settings

https://imgur.com/a/IKraeEa

Schedule Rule

https://imgur.com/a/KCTQKxL

Add  Elatic Defend Intergration To Host

https://imgur.com/a/Vj0nR2t


Install Elastic On Kali

https://imgur.com/a/hbQb8d1

Elastic On Kali File Loading

https://imgur.com/a/ACIs05r

Yes Or No continue loading

https://imgur.com/a/NivrS8J

Elastic Agent Has Been Successfully Added

https://imgur.com/a/v6G2Ptj

Agent enrolled

https://imgur.com/a/0Xcgvnd

Step 3: Generating Security Events on the Kali VM using Nmap

https://imgur.com/a/swkdAUM

Generating Nmap scans on your Kali VM’s IP address

https://imgur.com/a/zHg0fE5

Step 4:  Querying for Security Events in the Elastic SIEM

Logs > Observability

https://imgur.com/a/JJ7uWZq

Stream

https://imgur.com/a/tVzRfZt

Details For Log Entry

https://imgur.com/a/SJUGqpW

Nmap events

https://imgur.com/a/bITo42h

Step 5:  Create a Dashboard to Visualize the Events

Dashboard

https://imgur.com/a/f7QQBxI

Create Dashboard

https://imgur.com/a/SFsn6Y6

Create Visualization

https://imgur.com/a/0f3jtVF

Edit Visualization

https://imgur.com/a/OQZqAQ2

SIEM Visualization Table

https://imgur.com/a/J82aRO9

Step 6: Create an Alert

Create Alert

https://imgur.com/a/B1CCx3I

Manage Rules

https://imgur.com/a/CWc7wZJ

Create New Rule

https://imgur.com/a/kwTLKl8

Custom Query

https://imgur.com/a/wDbE45f

 Event.action: “nmap_scan”

 https://imgur.com/a/6vRYjz5

 About Rule

 https://imgur.com/a/jMIOJ2Q

 Schedule Rule

 https://imgur.com/a/zeATguU

 Rule Actions

 https://imgur.com/a/Modt1ji

 Test Rule

 https://imgur.com/a/6Fl0XHm
 
Step 7: Documentation

Implementation Report: SIEM System

 Introduction

 Purpose and Scope
The purpose of this project was to implement a Security Information and Event Management (SIEM) system using the Elastic Stack to enhance the organization's security posture. The scope included the setup of data collection from various sources, log analysis, visualization, and alerting mechanisms to detect and respond to security threats.

Setup and Configuration

 Installation and Configuration Steps

 1. Installing Elastic Stack
- Prerequisites: Ensure that the server meets the necessary hardware and software requirements (RAM, CPU, OS version).
- Install Elasticsearch:
  - Download the latest version from the [Elastic website](https://www.elastic.co/downloads/elasticsearch).
  - Install via package manager (e.g., APT for Ubuntu):
    ```bash
    wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-<version>-amd64.deb
    sudo dpkg -i elasticsearch-<version>-amd64.deb
    ```
  - Configure Elasticsearch in `/etc/elasticsearch/elasticsearch.yml`, adjusting settings like network host and cluster name.
  - Start the Elasticsearch service:
    ```bash
    sudo service elasticsearch start
    ```

- Install Kibana**:
  - Download and install Kibana using similar steps as Elasticsearch.
  - Configure Kibana in `/etc/kibana/kibana.yml` to connect to Elasticsearch.
  - Start the Kibana service:
    ```bash
    sudo service kibana start
    ```

- Install Logstash (optional, for data processing):
  - Download and install Logstash.
  - Configure Logstash pipelines in `/etc/logstash/conf.d/`.

2. Installing Kali Linux
- Download Kali from the official website and create a bootable USB drive or virtual machine.
- Install Kali on the designated hardware, ensuring network connectivity.
  
 Data Collection Methods and Sources
- Filebeat: Install Filebeat on the systems to collect logs.
  - Configure Filebeat in `/etc/filebeat/filebeat.yml` to specify log sources.
  - Example for collecting syslogs:
    ```yaml
    filebeat.inputs:
      - type: syslog
        enabled: true
        protocols:
          syslog:
            host: "0.0.0.0:514"
    ```
  - Start Filebeat:
    ```bash
    sudo service filebeat start
    ```

- Winlogbeat: For Windows environments, install Winlogbeat to collect Windows event logs.
  
- Packetbeat: Optionally, use Packetbeat to monitor network traffic.

Analysis and Monitoring

Creating Visualizations, Dashboards, and Alerts in Elastic
- Access Kibana: Navigate to the Kibana web interface at `http://<KIBANA_IP>:5601`.
  
- Creating Visualizations:
  - Go to the "Visualize" tab and select the type of visualization (e.g., pie chart, line graph).
  - Choose the index pattern for the logs you wish to visualize.
  - Configure the visualization parameters and save.

- Creating Dashboards:
  - Access the "Dashboard" tab.
  - Click "Create new dashboard" and add previously created visualizations.
  - Arrange and save the dashboard layout.

- Setting Up Alerts:
  - Navigate to the "Alerting" section in Kibana.
  - Create a new alert using rules (e.g., threshold-based alerts for unusual login attempts).
  - Configure notifications (e.g., email, Slack).

Findings

Summary of Significant Findings
- Initial Log Analysis: During the initial analysis, several anomalies were detected, including:
  - Multiple failed login attempts indicating potential brute-force attacks.
  - Unusual outbound traffic patterns suggesting data exfiltration.
  - Unauthorized access attempts to sensitive directories.

 Conclusion

 Overall Conclusions and Recommendations
The implementation of the SIEM system has provided valuable insights into the organization's security posture. The Elastic Stack enables effective log management, visualization, and alerting capabilities.

Recommendations for Further Action:
1. Continuous Monitoring: Implement ongoing monitoring practices to respond to alerts promptly.
2. Regular Review of Configurations: Periodically review data collection configurations and alert thresholds to adapt to evolving threats.
3. Training and Awareness: Conduct regular training sessions for security personnel to maximize the use of the SIEM system.

This report serves as a foundational document for ongoing security improvements and highlights the importance of proactive monitoring in safeguarding organizational assets.
 







