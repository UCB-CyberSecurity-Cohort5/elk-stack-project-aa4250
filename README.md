# ELK-Stack-Project
Project 1 - ELK Stack Project

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

 https://github.com/UCB-CyberSecurity-Cohort5/elk-stack-project-aa4250/blob/48621ecb57910daeb1420b55654ef608b0823d98/Diagrams/Project1_13Homework.drawio.png


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

-	/etc/ansible/my-elk.yml


This document contains the following details:
-	Description of the Topology
-	Access Policies
-	ELK Configuration
o	Beats in Use
o	Machines Being Monitored
-	How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
-	What aspect of security do load balancers protect? 
o	Load balancers protects the system from DDoS attacks by shifting attack traffic.

-	What is the advantage of a jump box? 
o	The advantage of a JumpBox is the start point for administrator or individual that need to configure any other devices on the network. 


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
-	What does Filebeat watch for? 
o	Filebeat watches for any information in the file system which has been changed and when it has. 
o	Filebeat watches for log files/locations and collects log events

-	What does Metricbeat record? 
o	Metricbeat takes the metrics and statistics that collects and ships them to the output you specify. 
o	Metricbeat records metric and statistical data from the operating system and from services running on the server.








The configuration details of each machine may be found below.
Name	Function	IP Address	Operating System
JumpBox	Gateway	10.0.0.4	(Linux18.04)
Web-1	Server	10.0.0.5	(Linux18.04)
Web-2	Server	10.0.0.6	(Linux18.04)
Web-3	Server	10.0.0.7	(Linux18.04)
Elk-VM1	Elk Server	10.1.0.4	(Linux18.04)

--- Access Policies ---

The machines on the internal network are not exposed to the public Internet. 

Only the JUMPBOX machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-	My public WAN IP address could only access my jumpbox 

Machines within the network can only be accessed by SSH.
-	Which machine did you allow to access your ELK VM? 
o	My public WAN IP address could only access my Elkserver 
o	My Jumpbox could access the ELK server as well using 10.0.0.4
-	What was its IP address? 
o	My public IP address is 137.135.115.14

A summary of the access policies in place can be found in the table below.

Name	Publicly Accessible	Allowed IP Addresses
Jump Box	NO	10.0.0.4
Web-1	NO	10.0.0.5
Web-2	NO	10.0.0.6
Web-3	NO	10.0.0.7
Elk-VM1	NO	10.1.0.4

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-	What is the main advantage of automating configuration with Ansible? 
o	It allows you to configure multiple server / devices using a simple script 

The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
-	Install docker.io
-	Install Python-pip
-	Install docker container
-	Launch docker container: elk
-	Command: sysctl -w vm.max_map_count=262144-

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

 https://github.com/UCB-CyberSecurity-Cohort5/elk-stack-project-aa4250/blob/705c2ef32719d077413e2f94023f05059b4e86b1/Diagrams/dockerps.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-	Web-1(10.0.0.5) Web-2(10.0.0.6) and Web-3(10.0.0.7)

We have installed the following Beats on these machines:
-	Specify which Beats you successfully installed 
o	Successfully installed:- - Filebeat - Metricbeat

These Beats allow us to collect the following information from each machine:
-	Filebeat monitors log files or locations you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
-	Metricbeat collects metrics from the operating system and from services running on the server.

--- Using the Playbook ---
To use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible/
- Update the configuration file to include – Webserver and ELK server IP address (Private)
- Run the playbook and navigate to ELK VM to check that the installation worked as expected.
/etc/ansible/host should include:
[webservers]
 [10.0.0.5] ansible_python_interpreter=/usr/bin/python3 
[10.0.0.6] ansible_python_interpreter=/usr/bin/python3 
[10.0.0.7] ansible_python_interpreter=/usr/bin/python3
[elk] 
[10.1.0.4] ansible_python_interpreter=/usr/bin/python3
To run the playbook, you need to SSH into the Elk VM, then run docker ps to check that the installation worked as expected. My playbook file: my-elk.yml is location at: /etc/ansible/my-elk.yml 
Navigate to http://52.190.186.106:5601/app/kibana to confirm ELK and kibana are running. You may need to try from multiple web browsers Click 'Explore on Your Own' and you should see the following:
 


Answer the following questions to fill in the blanks:
-	Which file is the playbook?   Where do you copy it?
o	/etc/ansible/filebeat-configuration.yml

-	Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? 
o	I edited the /etc/ansible/hosts file to add webserver/elkserver ip addresses to it

-	Which URL do you navigate to in order to check that the ELK server is running?
o	http://52.190.186.106:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

-	ssh Redadminn@JumpBox(Public IP)
-	sudo docker container list -a (locate your ansible container)
-	sudo docker start container (name of the container)
-	sudo docker attach container (name of the container)

