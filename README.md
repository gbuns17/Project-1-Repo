## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

! ~/Documents/School/Project-1-Repo/Diagrams/'Project 1 Diagram.png'

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yaml file may be used to install only certain pieces of it, such as Filebeat.

  -  install-elk.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly stable, in addition to restricting access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?
Load balancers protect against overwhelming a server or network with traffic and can help prevent denial of service attacks. 
The advantage of a jump box is to have one machine to access all of your subnetworks or attached virtual machines or containers without having to boot from multiple devices.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the permissions and system network.
- _TODO: What does Filebeat watch for? Changes to files and file access.
- _TODO: What does Metricbeat record? Metric data like time spent on a machine etc.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web-1    |    VM    |  10.0.0.5  |  Linux           |                  
| Web-2    |    VM    | 10.0.0.6   | Linux            |
|ElK-Server|Monitoring| 10.1.0.5   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 71.229.132.122
- _TODO: Add whitelisted IP addresses 71.229.132.122, 
168.62.10.181

Machines within the network can only be accessed by Jump-Box.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address? Jump-Box, 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
|ELK-Server| No                  | 10.0.0.4             |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it is much faster and easier to pinpoint errors or typos made etc.
- _TODO: What is the main advantage of automating configuration with Ansible? It completes all the neccesary steps to set up a program at one time and gives you specific details if something goes wrong instead of going step-by-step.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc. 
- Install docker.io
- Install pip3
- Install Docker Python module
- Use more memory
- Download and launch ELK docker container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

! ~/Documents/School/Project-1-Repo/README/Images/'check docker on ELK.PNG'

### Target Machines & Beats
This ELK server is configured to monitor the following machines: Web-1, Web-2
- _TODO: List the IP addresses of the machines you are monitoring 10.0.0.5 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Information kept in log files or other specified logs.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to /etc/ansible/.
- Update the playbook file to include Download and install filebeat.deb, drop in filebeat.yml, enable and configure system module, setup filebeat, start filebeat.
- Run the playbook, and navigate to ELK-Server vm to check that the installation worked as expected.

- _Which file is the playbook? filebeat-playbook.yml, copied to /etc/ansible/roles in the ansible docker container.
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
ansible.cfg, change the host to the remote user of the ELK vm in this case azadmin.
- _Which URL do you navigate to in order to check that the ELK server is running?
http://[elk-vm-ip]:5601/kibana/home
