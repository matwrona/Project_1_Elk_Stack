## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Images/network_diagram.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible playbook file may be used to install only certain pieces of it, such as Filebeat.



This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly resilient, in addition to restricting access to the network.
Load balancers protect the Availability aspect of cybersecurity, ensuring that the servers (and website) remains online and available. Using a jumpbox for administration allows you to decrease the attack surface and decrease the risk of total compromise.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the filesystem and system access.
Filebeat is used for monitoring server logs, while metricbeat logs the services running on a server

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name       | Function       | IP Address | Operating System |
|------------|----------------|------------|------------------|
| Jump Box   | Gateway        | 10.0.0.4   | Linux            |
| Elk Server | Log collection | 10.1.0.4   | Linux            |
| Web1       | DVWA webserver | 10.0.0.8   | Linux            |
| Web2       | DVWA webserver | 10.0.0.9   | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 13.90.103.142

Machines within the network can only be accessed by ssh.
- the jumpbox machine is the only computer allowed to accked the machines within the network (through ssh). Its IP is 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|-----------|---------------------|----------------------|
| Jump Box  | Yes                 | 13.90.103.142        |
| Elk server| NO                  | 10.0.0.4             |
|           |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it is highly scalable to any number of computers, and it saves time by eliminating the need to configure each machine separately and individually.



The playbook implements the following tasks:
- installs docker
- install the python dependency for pip3
- download the pip module 
- allocate more memory to ensure docker runs properly
- download and launch the elk module

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

**Note**: The following image link needs to be updated. Replace `docker_ps_output.png` with the name of your screenshot image file.  


![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.8 and 10.0.0.9

We have installed the following Beats on these machines:
- metricbeat and filebeat

These Beats allow us to collect the following information from each machine:
- system access, service status, networking activity

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the my-playbook file to the playbook directory.
- Update the my-playbook file to include the correct ip addresses for the machines you have deployed. Use the hosts file to create and elk server group, and a webservers group.
- Run the playbook, and navigate to the load balancer public IP (or URL if applicable) to check that the installation worked as expected.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
