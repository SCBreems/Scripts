## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/SCBreems/Scripts/blob/f1bc3cb4c9db58268f5a8af850f3151298a1ab80/Diagrams/Seth%20Breems%20Unit%2013-Elk.drawio.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  https://github.com/SCBreems/Scripts/blob/f1bc3cb4c9db58268f5a8af850f3151298a1ab80/Ansible/filebeat-playbookyml.txt

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.

- Load Balancers ensures availability through redunceny and protects organizations from distributed denial-of-servive attacks by distributing network traffic across multiple servers. Jump-Box servers act as a single point of access to machines within the network, thus increasing security as incoming and outgoing traffic within the network can be monitored through a single focal point.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system logfiles and system usage.

-_What does Filebeat watch for?_

- Filebeat watches for logfiles & log events.

-_What does Metricbeat record?_

- Metricbeat records CPU usage, memory usage, memory rss, as well as many other statistics for processes that are running on the system that is being monitored.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump-Box-Provisioner | Gateway | 20.213.110.118 / 10.0.0.12 | Linux |
| Web-1 | Web Server | 10.0.0.13 | Linux |
| Web-2 | Web Server | 10.0.0.14 | Linux |
| Web-3 | Web Server | 10.0.0.15 | Linux |
| Elk-Server | Log Analytics | 13.67.181.198 / 10.1.0.5 | Linux |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 98.240.156.200

Machines within the network can only be accessed by Jump-Box-Provisioner.

The only machine that had access to the ELK VM was the Jump Box Provisioner with the IP address of 10.0.0.12

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump-Box-Provisioner | Yes | 98.240.156.200 (ssh):22 / (http):80 |
| Web-1 | No | VirtualNetwork / 10.0.0.4:22 |
| Web-2 | No | VirtualNetwork / 10.0.0.4:22 |
| Web-3 | No | VirtualNetwork / 10.0.0.4:22 |
| Elk-Server | Yes | VirtualNetwork / 98.240.156.200:5601 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
Ansible improves efficiency, management, and scalability by allowing you to manage all of your servers at once instead of managing each server one by one.

The playbook implements the following tasks:
- First, you want to configure the Elk VM with Docker.
- Secondly, you want to install docker.io & python3-pip.
- Third, you want to install the docker module.
- Lastly, you want to download the sebp/elk:761 image.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/SCBreems/Scripts/blob/3fb1d8e4fe5f183880e09a0192222fce6885e0da/Images/ElkRunning-Screenshot.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.13
- Web-2 10.0.0.14
- Web-3 10.0.0.15.

We have installed the following Beats on these machines:
- Filebeat & Metricbeat

These Beats allow us to collect the following information from each machine:
- FileBeat collects log & file data which can be used to monitor and track any unusual behaviour. Filebeat will allow you to view syslog events from each individual host in real time.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk-playbook.yaml file to ansible containers file.
- Update the ansibles hosts file to include...
- Run the playbook, and navigate to http://13.67.181.198:5601/app/kibana to check that the installation worked as expected.

> As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.

1. SSH into the Jump-Box-Provisioner.

`ssh scbredteam@20.213.110.118`

2. Start and then attach to your ansible container.

`sudo docker container list -a`  
`sudo docker container start elated_chebyshev`  
`sudo docker container attach elated_chebyshev`  

3. Edit the ansible hosts file.

`nano /etc/ansible/hosts`  

4. Edit the host file by adding [elk] as a group, the Elk-Server's internal IP ao that ansible can locate and connect to it, and then set python as default.

*[elk]  
10.1.0.5 ansible_python_interpreter=/usr/bin/python3*

5. Create the yml file in order to install elk.

`cd /etc/ansible`  
`touch install-elk.yml` 

https://github.com/SCBreems/Scripts/blob/3fb1d8e4fe5f183880e09a0192222fce6885e0da/Ansible/install-elkyml.txt

`/etc/ansible# ansible-playbook elk.yml`  