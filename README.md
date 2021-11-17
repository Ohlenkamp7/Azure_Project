## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the ansible folder may be used to install only certain pieces of it, such as Filebeat.

![Filebeat Yml file](Azure_Project/Ansible/filebeat-playbook.yml) 

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly dependable, in addition to restricting attacks to the network.

Our load balancer will help ensure that our servers will have high availablity and it will be harder to have our network completely down. 
The advantage of our Jump Box is simply that it restricts our access to our network and only allows access from specific machines, or in this projects case our personal machine. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files, logs and system processes.
Filebeat watchs for file and account changes
Metricbeat records our system proformance and changes to our systems

The configuration details of each machine may be found below.

| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jump Box | Gateway   | 10.0.0.1   | Linux            |
| RT-PC1   | DVWA      | 10.0.0.7   | Linux            |
| RT-PC2   | DVWA      | 10.0.0.8   | Linux            |
|Elk Server| Monitoring| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP address:
Your Personal IP


Machines within the network can only be accessed by our Ansible machine in our Jump Box.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Personal IP Address  |
| RT-PC1   | No                  | 52.183.85.249        |
| RT-PC2   | No                  | 52.183.85.249        |
|Elk Server| No                  | 52.183.85.249        |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because you can configure multiple machines simulataniously and efficiantly. Running one script allows you to install a bunch of software all over your network.

The playbook implements the following tasks:
- Installs and enable docker on boot
- Installs python and makes it so you can run python scripts
- Installs and runs Elk container
- Increases memory used as not to bottleneck your Docker modules


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Successful Docker Implementation](Diagrams/docker_ps)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:



We have installed the following Beats on these machines:
MetricBeat
FileBeat

These Beats allow us to collect the following information from each machine:
Filebeat is to collect all file changes and logs that the machines make. Metricbeat allows us to collect all machine data such as CPU usage.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk-install.yml, metricbeat-install.yml, and filebeat-install.yml files to /etc/ansible/ directory.
- Update the hosts file to include all hosts that will have the playbooks installed on them. 
- Run the playbook, and navigate to updated hosts to check that the installation worked as expected.




