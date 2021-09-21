# Cloud-Security
This repository outlines a project including an AZURE based cloud network
[README.md](https://github.com/Stattixz/Cloud-Security/files/7200466/README.md)
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Images/Project 1 Cloud Network.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

Cloud-Security/Ansible/Filebeat-playbook.yml

../Ansible/metricbeat-playbook.yml

../Ansible/install-ELK.yml

../Ansible/web_server_setup.yml


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting unauthorized access to the network.
-What aspect of security do load balancers protect? What is the advantage of a jump box?
   One of the main purposes of the load balancer is to protect against Destributed Denial of Service (DDOS) attacks. In addition, having a jump box significantly increases the security of a network. This is because the jump box is the only way to make administrative chages to the connected servers. Admins must connect to the jump box before they can make any changes to the system.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the mettrics and system logs.
-What does Filebeat watch for?_ filebeat monitors the specified log files and locations and sends the events to logstash or elasticstash to be indexed.
-What does Metricbeat record?_ Metricbeat collects metrics from the operating system and services running on the server and sends the data to be indexed.

The configuration details of each machine may be found below.

| Name     | Function      | IP Address | Operating System |
|----------|---------------|------------|------------------|
| Jump Box | Gateway       | 10.0.0.4   | Linux            |
| ELK      | Sys logs      | 10.1.0.4   | Linux            |
| Web-1    | Run website   | 10.0.0.5   | Linux            |
| Web-2    | Backup server | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Load Balancer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
10.0.0.5
10.0.0.6

Machines within the network can only be accessed by The Jump Box.
 it has an IP of 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible | Allowed IP Addresses |
|---------------|---------------------|----------------------|
| Jump Box      | No                  | 10.0.0.1  10.0.0.2   |
| ELK           | no                  | 10.0.0.5  10.0.0.6   |
| Load Balancer | yes                 | all                  |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows for faster and more accurate distributions and setups.

The playbook implements the following tasks:
- ... The first step in the playbook tells it to install Docker.io and pull the required image file. 
- ... Then it increases the amount of virtual memory used.
- ... Finally it downloads and launches a docker elk container.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeats collects system type events such as logins to see who is actively logging into the system 
- Metricbeats collects useful information such as cpu usage and memory, this is useful to have because it allows us to check the system to make sure it is healthy and keep it safe and secure. 
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-ELK.yml file to /etc/ansible/install-ELK.yml.
- Update the hosts file to include ELK with its destination IP.
- Run the playbook, and navigate to http://[your_elk_server_ip]:5601/app/kibana to check that the installation worked as expected.
