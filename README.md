## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

RM_projects/Diagrams/Cloud_Security_Diagram

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - elkdocker1.yml_

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____reliable, in addition to restricting _____access to the network.
- _TODO: What aspect of security do load balancers protect? Load balancers protect servers from overloading and helps the data move more efficiently.  What is the advantage of a jump box?_ The advantage of a jump box is that it is a secure computer that all administrators connect to first before completing administrative tasks on the network.  That way no administration tasks take should be completed outside of the jump box.  

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____system and system _____ logs.
- _TODO: What does Filebeat watch for?_ Filebeatmonitors logs or locations specified and collects logged events and sends them to Elasticsearch or Logstash for examination and analysis.   
- _TODO: What does Metricbeat record?_ Metricbeat collects metrics and statistics from the operating system and services and then send them to Elasticsearch or Logstash for examination and analysis. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name       | Function    | IP Address    | Operating System |
|------------|-------------|---------------|------------------|
| Jump Box   | Gateway     | 40.112.215.72 | Linux            |
| Web1       | HTTP Traffic| 10.0.0.5      | Linux            |
| Web2       | HTTP Traffic| 10.0.0.6      | Linux            |
| ELK Server | ELK Server  | 52.170.18.55  | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box (JBox) machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_ 99.234.52.128

Machines within the network can only be accessed by the Jump Box (JBox).
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_ My personal machine is the only machine that has access to The ELK server.  The IP address of the ELK machine is 52.170.18.55 

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses |
|-----------|---------------------|----------------------|
| Jump Box  | Only w/public key   | 99.234.52.128.       |
| Web1      | No                  |                      |
| Web2      | No                  |                      |
| Elk Server| Yes

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because its saves time by automating tasks.

- _TODO: What is the main advantage of automating configuration with Ansible?_ The main advantage is time saving.  Instead of administrators spending a lot of time configuring machines manually with Ansible it can be a quick task.  It can also reduce bugs as the playbook configuration would be consistent.   

??????The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._ how do playbooks work how do they install each of these things focus on elk playbook and dvwa playbook
- Created new virtual network (ELK network), in a new region and within the existing resource group
- Created a peer connection to the existing virtual network 
- Created a new virtual machine (ELK) within the new virtual network, and its own security group.
- Downloaded and configured ELK-Docker onto the new virtual machine...From Ansible container added new VM to host file.  Created a playbook that installs and configures the container.
- Launched and exposed the ELK-Docker container
- Restricted access and added public IP addrress to whitelist in the ELK Network security Group 
 

???The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

Web1 13.64.128.17
Web2 13.64.128.17

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
Web1 - Filebeat
Web2 - Filebeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

???### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a 	control node provisioned: 

???SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._