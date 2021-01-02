## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

RM_projects/Diagrams/Cloud_Security_Diagram

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - elkdocker1.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting access to the network.
- What aspect of security do load balancers protect? Load balancers protect servers from overloading and helps the data move more efficiently.  What is the advantage of a jump box?_ The advantage of a jump box is that it is a secure computer that all administrators connect to first before completing administrative tasks on the network.  That way no administration tasks take should be completed outside of the jump box.  

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system and system logs.
- What does Filebeat watch for? Filebeatmonitors logs or locations specified and collects logged events and sends them to Elasticsearch or Logstash for examination and analysis.   
- What does Metricbeat record? Metricbeat collects metrics and statistics from the operating system and services and then send them to Elasticsearch or Logstash for examination and analysis. 

The configuration details of each machine may be found below.

| Name       | Function    | IP Address    | Operating System |
|------------|-------------|---------------|------------------|
| Jump Box   | Gateway     | 40.112.215.72 | Linux            |
| Web1       | HTTP Traffic| 10.0.0.5      | Linux            |
| Web2       | HTTP Traffic| 10.0.0.6      | Linux            |
| ELK Server | ELK Server  | 52.170.18.55  | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box (JBox) machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Add whitelisted IP addresses_ 99.234.52.128

Machines within the network can only be accessed by the Jump Box (JBox).
- Which machine did you allow to access your ELK VM? What was its IP address? My personal machine is the only machine that has access to The ELK server.  The IP address of the ELK machine is 52.170.18.55 

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses |
|-----------|---------------------|----------------------|
| Jump Box  | Only w/public key   | 99.234.52.128.       |
| Web1      | No                  |                      |
| Web2      | No                  |                      |
| Elk Server| Yes

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because its saves time by automating tasks.

- What is the main advantage of automating configuration with Ansible? The main advantage is the time savings.  Instead of administrators spending a lot of time configuring machines manually with Ansible it can be a quick task.  It can also reduce bugs as the playbook configuration would be consistent.   

The playbook implements the following tasks:
- In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc. How do playbooks work how do they install each of these things focus on elk playbook and dvwa playbook
- Created new virtual network (ELK network), in a new region and within the existing resource group
- Created a peer connection to the existing virtual network 
- Created a new virtual machine (ELK) within the new virtual network, and its own security group.
- Downloaded and configured ELK-Docker onto the new virtual machine.  From Ansible container added new VM to host file.  Created a playbook that installs and configures the container, which added DVWA.
- Launched and exposed the ELK-Docker container
- Restricted access, added public IP address to whitelist in the ELK Network security Group, and opened ports 5601 and port 9200 for Elasticsearch and Kibana services. 
 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

!Image 2020-12-29 at 2.55 PM.jpeg

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring

Web1 13.64.128.17
Web2 13.64.128.17

We have installed the following Beats on these machines:
- Specify which Beats you successfully installed
Web1 - Filebeat
Web2 - Filebeat

These Beats allow us to collect the following information from each machine:
- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

Filebeat monitors log files or specific locations, then collects those events and then sends them to Elasticsearch or Logstash.  The data is easily visualized in Kibana 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy Public key file to the target VM
- Update the host file to include the domain of the target VM's
- Run the playbook, and navigate to target VM to check that the installation worked as expected


_Answer the following questions to fill in the blanks:_
- _Which file is the playbook? elkdocker1.yml is the playbook. Where do you copy it?_ It is copied into /etc/ansible
- _Which file do you update to make Ansible run the playbook on a specific machine? You update the host file.

How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ This is defined in the playbook.
- Which URL do you navigate to in order to check that the ELK server is running? http://[your.ELK-VM.External.IP]:5601/app/kibana

As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
