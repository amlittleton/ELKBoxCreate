# ELKBoxCreate
Create an ELK Box on any VM
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagram/project1-3.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - filebeat-playbook.yml._

This document contains the following details:
- Description of the Topologue
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly accessible, in addition to restricting access to the network.
- What aspect of security do load balancers protect? Accessibility.  What is the advantage of a jump box? It's the only place where you can make changes to the system and will download to the rest of the VM's connected to it.  

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the CPU and system logs.
- What does Filebeat watch for? It monitors log files or locations that you specify, collects log events, and forwards the to either Elasticsearch or Logstash for indexing.
- What does Metricbeat record? It sends system and service statistics.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function     | IP Address | Operating System |
|----------|--------------|------------|------------------|
| Jump Box | Gateway      | 10.0.0.4   | Linux            |
| Web-1    |DVWA Container| 10.0.0.5   | Linux            |
| Web-2    |DVWA Container| 10.0.0.6   | Linux            |
| Web-3    |DVWA Container| 10.0.0.7   | Linux            |
| ElkBox   |Elk Container | 10.1.0.4   | Linux            |



### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: 72.220.60.185_

Machines within the network can only be accessed by JumbBox.
- _TODO: Which machine did you allow to access your ELK VM? JumpBox What was its IP address? 10.0.0.4_

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 72.220.62.185        |
| Elk Box  | No                  | 72.220.62.185        |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible? Increased productivity and efficiency.

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install Docker
- Install Python 3pip
- Install Docker Module
- Install docker ELK container
- run the filebeat-playbook.yml.


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

!(Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5 - 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors log files or locations that are specified by you.  It collects log events and forwards the either to Elasticsearch or Logstash for indexing.
- Metricbeat can periodically collect metrics from the operating system and from services running on the server.  Takes metrics and statistics that was collected and ships them to the output you specificy, such as Elasticsearch or Logstash.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to /etc/filebeats.
- Update the filebeat-config.yml file to include the servers you are monitoring and the main ELK server.
- Run the playbook, and navigate to http://52.152.130.112:5601/app/kibana#/home/tutorial/systemLogs to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? filebeat-playbook.yml  Where do you copy it? /etc/filebeat/filebeat.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? install-elk.yml  How do I specify which machine to install the ELK server on versus which to install Filebeat on?_Adding the private IP to the hosts files and linking it ot the right yml file.  For the filebeat, you need to edit the filebeat-config.yml file and add the private IPs of the VM's you want to log.
- _Which URL do you navigate to in order to check that the ELK server is running? http://52.152.130.112:5601/app/kibana#/home/tutorial/systemLogs

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
