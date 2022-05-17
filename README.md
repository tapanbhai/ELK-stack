# ELK-stack
## Project 1 Hw13


PLAYBOOK/CONFIGURATION FILES
•	Filebeat
•	Metricbeat
•	ELK-server
•	my-playbook
•	Metricbeat-Config
•	Filebeat-Config
This document contains the following details:
•	Description of the Topology
•	Access Policies
•	ELK Configuration
o	Beats in Use
o	Machines Being Monitored
•	How to Use the Ansible Build


## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

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

Load balancing ensures that the application will be highly Available, in addition to restricting Access to the network.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_fwding all the log data
- _TODO: What does Metricbeat record?_operating systems and service metrics

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     	 | Function 	| IP Address | Operating System |
|----------	 |----------	|------------|------------------|
| Jump Box 	 | Gateway  	| 10.0.0.1   | Linux            |
| Web1=DVWA1     | Web server   | 10.0.0.8   | Linux            |
| Web2=DVWA2     | Web server   | 10.0.0.9   | Linux            |
| vmelk1=ELK     | Monitoring   | 10.1.0.4   | Linux            |
