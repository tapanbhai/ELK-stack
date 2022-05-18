# ELK-stack
## Project 1 Hw13 Cloud Security


## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

ELK-stack/Diagrams/ELK-stack Project.drawio.png

![Elk-stack Project](Diagrams/ELK-stack%20Project.drawio.png)



These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology
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

A summary of the access policies in place can be found in the table below.

| Name     	| Publicly Accessible | Allowed IP Addresses |
|----------	|---------------------|----------------------|
| Jump Box 	| 	Yes           | My public IP  SSH22     |
| Web1=DVWA1    |     	NO            | 10.0.0.1-254  SSH22     |
| Web2=DVWA2    |       NO            | 10.0.0.1-254  SSH22     |
| ELKVM		|  	NO	      | 10.0.0.1-254  TCP5601	     |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
•	The main advantage of automating configuration with Ansible are as follows: ADVANTAGES OF ANSIBLE:

o	Open Source Tool

o	Ansible is an opensource tool without any paid licence needed and it can be used as free of cost.

o	Simple Configuration Management

o	Ansible can manage easily and learn easily. The shell scripts are simple and no need for any other software installed.

o	Application Development
o	It can easily deploy multi-tier applications. There is no need to configure applications on every machine, you have to only specify the tasks in the playbook. When we run the playbook, then it will automatically run the tasks in the playbook to each host machine through SSH.

o	The Playbooks are Written in YAML
o	The playbooks are Ansible configuration files that are written in YAML and use of it makes the Ansible better by configuration and automation tool.

o	No Agents Required
o	There is no need of agents or software when you want to automate with the client system or hosts.
o	Cloud Provisioning
o	By using Ansible we can cloud platforms and virtualized hosts , network devices etc.

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.

## 	Specify a different group of machines:

```
- name: Config elk VM with Docker
	    hosts: elk
	    become: true
	    tasks:
```

## Install Docker.io

```
- name: Install docker.io
     apt:
     update_cache: yes
     force_apt_get: yes
     name: docker.io
     state: present
```

## Installs Python3-pip

```
- name: Install python3-pip
     apt: 
     force_apt_get: yes 
     name: python3-pip 
     state: present 
```

## Use pip module (It will default to pip3)

```
- name: Install Docker module
     pip:
     name: docker
     state: present
     `docker`, which is the Docker Python pip module.      
```

## Increase Virtual Memory

```
- name: Use more memory
        sysctl:
        name: vm.max_map_count
        value: '262144'
        state: present
        reload: yes
```

## Download and Launch ELK Docker Container (image sebp/elk)

```
- name: Download and launch a docker elk container
    docker_container:
    name: elk
    image: sebp/elk:761
    state: started
    restart_policy: always
```

## Published ports 5044, 5601 and 9200 were made available

```
- published_ports:
   -  5601:5601
   -  9200:9200
   -  5044:5044   
```

5601 (Kibana web interface)
9200 (Elasticsearch JSON interface)
5044 (Logstash Beats interface, receive logs from Beats such as Filebeat)

## JBOX


## ELK-SERVER

## WEB1

## WEB2

## Target Machines & Beats

This ELK server is configured to monitor the following machines: List the IP addresses of the machines you are monitoring

•	Web-1: 10.1.0.8

•	Web-2: 10.1.0.9

We have installed the following Beats on these machines:

•	Filebeat_module_status

•	Metricbeat_module_status

These Beats allow us to collect the following information from each machine:
•	TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., Winlogbeat collects Windows logs, which we use to track user logon events, etc. Filebeat will be used to collect log files from specfic files in particular Apache, Mircosoft Azure tools and web servers, MySQL databases #[screeshoot of filebeat module kibana dashboard]#

•	Filebeat_syslog_Dashboard

•	Metricbeat_Docker_overview_Dashboard

Metricbeat will be used to monitor VM stats, per cpu core stats, per filesystem stats, memory stats and network stats #[screenshot of Kibana Docker containers[metricbeat docker] ecs]# #[screenshot of Kibana Host overview[metricbeat docker-web-1] metrics] #[screenshot of Kibana Host overview[metricbeat docker-web-2] metrics]
•	[Metricbeat_Kibana_Docker_Host_Web-1_and_Web-2_Overview_and_Container_ECS] -screenshot


## Using The Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
Verify the Public IP address to see if it has changed. [What Is My IP?](https://www.whatismyip.com/) If changed then update the Security Rules that uses the My Public IPv4
SSH into the control node and follow the steps below:

•	Copy the YML file to ansible folder.

•	Update the config file to include remote user and port

•	Run the playbook, and navigate to kibana((Users IP address):5601 to check that the installation worked as expected.


## ELK VM Configuration

•	Run the playbook using this command : ansible-playbook /etc/ansible/install-elk.yml

•	/etc/ansible/hosts file (IP of the Virtual Machines).


## For Filebeat

## Download Filebeat playbook usng this command:

```
- Run: curl -L -O https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/Filebeat > /etc/ansible/filebeat-config.yml
```

•	Copy the - Filebeat-Config Config file to /etc/ansible

•	Update the filebeat-config.yml file to include the ELK private IP 10.1.0.8 as below from root@9ddf6fe7eb3f:~# nano /etc/ansible/filebeat-config.yml

## Configuration

```
output.elasticsearch:
  Boolean flag to enable or disable the output module.
  enabled: true

 Array of hosts to connect to.
 Scheme and port can be left out and will be set to the default (http and 9200)
 In case you specify and additional path, the scheme is required: http://localhost:9200/path
 IPv6 addresses should always be defined as: https://[2001:db8::1]:9200
 hosts: ["localhost:9200"]
 username: "elastic"
 "changeme" # TODO: Change this to the password you set
 Starting with Beats version 6.0.0, the dashboards are loaded via the Kibana API.
 This requires a Kibana endpoint configuration.
 setup.kibana:
  host: "10.0.0.8:5601" #### TODO: Change this to the IP address of your ELK server

```

## For MetricBeat

## Download MetricBeat playbook usng this command

```
Run: curl -L -O https://gist.githubusercontent.com/slape/5cc350109583af6cbe577bbcc0710c93/raw/eca603b72586fbe148c11f9c87bf96a63cb25760/metricbeat > /etc/ansible/metricbeat-config.yml
```

## Configuration

```
============================== Kibana =====================================
  Starting with Beats version 6.0.0, the dashboards are loaded via the Kibana API.
  This requires a Kibana endpoint configuration.
  setup.kibana:
  	host: "10.0.0.5:5601" 
  	
  -------------------------- Elasticsearch output ------------------------------ 
  output.elasticsearch: 
  - TODO: Change the hosts IP address to the IP address of your ELK server 
  - TODO: Change password from `changem` to the password you created 
   hosts: ["10.0.0.5:9200"] 
   username: "elastic" 
   password: "changeme"
   
   ```

Copy the - Metricbeat-Config
Update the metricbeat-config.yml file to include the ELK private IP 10.1.0.5 as below from root@9ddf6fe7eb3f:~# nano /etc/ansible/filebeat-config.yml


## Run the playbook using this command ansible-playbook filebeat-playbook.yml and navigate to Kibana 
