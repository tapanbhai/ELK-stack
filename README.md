# ELK-stack
## Project 1 Hw13 Cloud Security


## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)
Images/ELK_Network_Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
What aspect of security do load balancers protect?

•	Load balancing ensures that the application will be highly stable, in addition to restricting access to the network.

•	Load balancers improve application availability and responsiveness and prevent server overload.Load balancer defends an organization against distributed denial-of-service (DDoS) attacks

What is the advantage of a jump box?

•	A couple advantages of a jumpbox are: Improve Security: A jump box creates a separation between a user's workstation (which is at high risk of being compromised) and the privileged assets within the network. This separation helps to isolate privileged assets so that they aren't directly in contact with potentially compromised workstations. Because of their access to potentially sensitive areas, jump boxes are usually "hardened" in the extreme.

•	Improve Productivity: A jump box provides effective access control. It makes it possible for the admin to do their work on the two sub-networks without logging out and into each privileged area.

•	When a jump box is used, its hidden benefit is that any tools in place for the SAN system are maintained on that single system. Therefore, when an update to the SAN management software is available, only a single system requires the update. A Jump Box Provisioner is also important as it prevents Azure VMs from being exposed via a public IP Address.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Data and System logs.

•	What does Filebeat watch for?

Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing

•	What does Metricbeat record?

Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. Metricbeat helps you monitor your servers by collecting metrics from the system and services running on the server, such as: Apache



The configuration details of each machine may be found below.


| Name     	 | Function 	| IP Address | Operating System |
|----------	 |----------	|------------|------------------|
| Jump Box 	 | Gateway  	| 10.0.0.7   | Linux            |
| Web1=DVWA1     | Web server   | 10.0.0.8   | Linux            |
| Web2=DVWA2     | Web server   | 10.0.0.9   | Linux            |
| vmelk1=ELK     | Monitoring   | 10.1.0.4   | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox webserver machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _20.211.22.97= public ip of Jumpbox: Whitelisted IP addresses : Home ip addr, pvt ip of web1 = 10.0.0.8, web2 = 10.0.0.9 & vmelk1 = 10.1.0.4


Machines within the network can only be accessed by jumpbox webserver machine.
- 
Which machine did you allow to access your ELK VM?

The Jumpbox, Web1 & Web2 = Jumpbox, DVWA1 & DVWA2 via SSH port22

What was its IP address?_pvt ip 10.0.0.7, 10.0.0.8 & 10.0.0.9
