# vandyboot
Elk Stack Project

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below:

https://github.com/jmsmsln/vandyboot/blob/master/Diagrams/Elk%20Stack%20Diagram.drawio

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible Folder may be used to install only certain pieces of it, such as Filebeat.

  - https://github.com/jmsmsln/vandyboot/tree/master/Ansible

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting overloads to the network.
- A load balancer can be for security to protect confidentiality, integrity, and availability.  The advantage of using a Jump Box is to control access to a network and limit points of attack.  

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system and system applications.
- Filebeat monitors the log files.
- Metricbeat records metrics from the system and services running on the server.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name                 | Function   | IP Address | Operating System |
|----------------------|------------|------------|------------------|
| Jump-Box-Provisioner | Gateway    | 10.1.0.4   | Linux            |
| Web-1                | Server     | 10.1.0.5   | Linux            |
| Web-2                | Server     | 10.1.0.7   | Linux            |
| Elk-VM               | ELk Server | 10.0.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 68.47.253.74

Machines within the network can only be accessed by Jump-Box-Provisioner.
- The Jump-Box-Provisioner allows to access your ELK VM from the IP address 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses  |
|----------|---------------------|-----------------------|
| Jump Box | No                  | 68.47.253.74          |
| Web-1    | No                  | 10.1.0.4              |
| Web-2    | No                  | 10.1.0.4              |
| Elk-VM   | No                  | 10.1.0.4 68.47.253.74 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- there is less vulnerability of error.

The playbook implements the following tasks:
- Installs docker.io and python3-pip
- Increases virtual memory
- Downloads the image sebp/elk:761 
- Launches the docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance:

https://github.com/jmsmsln/vandyboot/blob/master/Images/Container%20on%20Elk%20Server%20is%20Running.jpg

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.1.0.5
- 10.1.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects log files of events that occur so that we have a record to refer to, i.e., opening a file or editing a file.
- Metricbeat collects metrics on server data, i.e., system-wide CPU and memory statistics.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Ansible/install-elk.yml file to /etc/ansible/install-elk.yml.
- Update the /etc/ansible/hosts file to include a new group called [elks] with the IP Address of the machine to deploy the Elk Stack "(IP Address) ansible_python_interpreter=/usr/bin/python3".
- Run the playbook, and navigate to http://[your.Elk-Machine.External.IP]:5601/app/kibana to check that the installation worked as expected. You should see the following page:

https://github.com/jmsmsln/vandyboot/blob/master/Images/Elk%20Server%20Access%20using%20Public%20IP%20Address.jpg
