## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/SCBreems/Scripts/blob/f1bc3cb4c9db58268f5a8af850f3151298a1ab80/Diagrams/Seth%20Breems%20Unit%2013-Elk.drawio.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  https://github.com/SCBreems/Scripts/blob/f1bc3cb4c9db58268f5a8af850f3151298a1ab80/Ansible/filebeat-playbookyml.txt

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.

Load Balancers ensures availability and protects organizations from distributed denial-of-servive (DDos) attacks by distributing network traffic across multiple servers. Jump Box servers act as a single point of access to machines within the network, thus increasing security as incoming and outgoing traffic within the network can be monitored through a single focal point.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system logfiles and system usage.

- _What does Filebeat watch for?_

Filebeat watches for logfiles & log events.

- _What does Metricbeat record?_

Metricbeat records CPU usage, memory usage, memory rss, as well as many other statistics for processes that are running on the system that is being monitored.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump-Box-Provisioner | Gateway  | 10.0.0.12   | Linux            |
| Web-1     |    Web Server      |     10.0.0.13       |         Linux         |
| Web-2     |     Web Server     |     10.0.0.14       |        Linux          |
| Web-3     |     Web Server     |      10.0.0.15      |         Linux         |
| Elk-Server     |     Log Analytics     |      10.1.0.5      |        Linux          |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 98.240.156.200

Machines within the network can only be accessed by Jump-Box-Provisioner.

The only machine that had access to the ELK VM was the Jump Box Provisioner with the IP address of 10.0.0.12

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._