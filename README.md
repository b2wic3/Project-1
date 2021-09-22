# Project-1
ucb-ELK-C13
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

<img src="Untitled Diagram.drawio.png">

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

<img src="Screen Shot 2021-09-21 at 9.16.28 PM.png">

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly availability, in addition to restricting DDoS attacks aiming to exceed the websites capacity to handle multiple requests to the network.
- Load balancers protects the system from DDoS attacks by shifting attack traffic. The advantage of a jumpbox is to give access to the user from a single node that can be monitored and secured.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
-Filebeat watches for information in the file system which has been changes and when it has. 
-Metricbeat takes and records the metrics and stats that collects and ships them to the output you choose.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Server   | 10.0.0.5   | Linux            |
| Web-2    | Server   | 10.0.0.6   | Linux            |
|day1-elkvm| Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the home machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 52.175.223.230

Machines within the network can only be accessed by VNET.
- JumpBox VM VNET IP 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 52.175.223.230       |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
|day1-elkvm| No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The main advantage is that you can put commands into multiple servers from a single playbook.

The playbook implements the following tasks:
- Install docker.io
- install python-pip
- install docker
- command- sysctl -w vm.max_map_count=262144
- launch docker container elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

<img src="Screen Shot 2021-09-21 at 4.24.35 PM.png">

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5 and 10.0.0.6

We have installed the following Beats on these machines:
- filebeat, metricbeat

These Beats allow us to collect the following information from each machine:
- Metricbeat collects metrics and stats, Filebeat forwards and centralizes data

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to the Web VMs.
- Update the host file to include webserver and elkserver ip addresses
- Run the playbook, and navigate to www.public:5601 to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- /etc/ansible/file/filebeat-playbook.yml
- edit the /etc/ansible/host files webserver/elkserver ip addresses
- www.publicip:5601

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
