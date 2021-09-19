# ELK-Stack-Deployment

The files in this repository were used to configure the network depicted below.


<img width="396" alt="Final Diagram" src="https://user-images.githubusercontent.com/84453422/133944974-6a9a2ae3-8cb2-490a-b72a-b3c261eb817f.PNG">


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

https://github.com/brvillan/ELK-Stack-Deployment/blob/main/Ansible/filebeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Load balancers will help to protect from DDoS attacks, as it distributes traffic to the servers. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system perfrormance.
- Filebeat monitors log files
- Metricbeat collects and sends metrics and statistics.

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| DVWA-VM1 |    VM    | 10.0.0.5   | Linux            |
| DVWA-VM2 |    VM    | 10.0.0.6   | Linux            |
| ELK-VM   | ElkStack | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 73.209.130.188

Machines within the network can only be accessed by port 22.
- 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 73.209.130.188       |
| DVWA-VMs | No                  | 10.0.0.4             |
| ELK Stack| No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Ansible is able to run from the command line, this ensures the scripts can run identically everywhere. 

The playbook implements the following tasks:
- Install docker.io
- Install python-pip
- Install docker python module
- Download and launch a docker ELK stack

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

<img width="672" alt="Docker ps" src="https://user-images.githubusercontent.com/84453422/133943839-32af85d1-15d3-4b5c-947b-4ea212e7e9d9.PNG">


### Target Machines & Beats
This ELK server is configured to monitor the following machines:

-10.0.0.5
-10.0.0.6

We have installed the following Beats on these machines:

-filebeat
-metricbeat

These Beats allow us to collect the following information from each machine:

-Filebeat monitors and collects log data on the specified servers. 

<img width="1911" alt="Kabana Filebeat" src="https://user-images.githubusercontent.com/84453422/133944723-f5997430-a929-495f-a826-ae90df01406b.PNG">

-Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify.

<img width="914" alt="metric" src="https://user-images.githubusercontent.com/84453422/133944896-4f47fe32-45eb-430d-a957-d4207ae9a56d.PNG">


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to the ELK VM in /etc/ansible/roles.
- Update the filebeat-config.yml file to include the webservers 10.0.0.5 and 10.0.0.6
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

