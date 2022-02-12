# Project-Elk
Elk Stack Project
The files in this repository were used to configure the network depicted below.

Cloud Security
![HW12](https://user-images.githubusercontent.com/90855483/153490534-106af00b-882f-494f-8ae5-2ae207a7580b.JPG)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  elk-playbook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Load balancers protects the system from DDoS attacks by shifting attack traffic. The advantage of a jump box is to give access to the user from a singe node that can be secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.
- Filebeat watches for any information in the file system which has been changed and when it has.
- Metricbeat takes the metrics and statistics that collects andships them to the output you specify.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Server   | 10.0.0.5   | Linux            |
| Web-2    | Server   | 10.0.0.9   | Linux            |
| Elk      | Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 75.166.99.33

Machines within the network can only be accessed by JumpBox.
- 20.127.131.175

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | Home IP              |
| Web-1    | No                  | 20.120.30.146        |
| Web-2    | No                  | 20.120.30.146        |
| Elk      | Yes                 | Home IP              |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The main advantage is the automation of the configuration.

The playbook implements the following tasks:

- docker.io
- Install pip3
- Install Docker python module
- increase virtual memory
- download and launch a docker elk docker_container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


![Elk](https://user-images.githubusercontent.com/90855483/153539515-b46b50b8-9518-4086-8421-148187cb2974.JPG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.5
- Web-2 10.0.0.9

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat system log management and collecting data like sudo commands, SSH logins, and new users and groups.
- Metricbeat is connected to dvwa and tracks CPU usage,memory, and number of containers.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the yml file to node.
- Update the host file to include IP addresses on the network.
- Run the playbook, and navigate to http://[ELK IP address]:5601/app/kibana to check that the installation worked as expected.


Which file is the playbook? Where do you copy it? 
- The playbook files are elk.yml, filebeat.yml, and metricbeat.yml. All of these files should be copied into the /etc/ansible folder.

Which file do you update to make Ansible run the playbook on a specific machine? 
- Update the host file to include two sections [elk] [webservers] with each having their respective VM IPs directly under them.

How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- Adding 'elk' or 'webservers' at the end of your playbook command will specify which machine the installation is intended for.

Which URL do you navigate to in order to check that the ELK server is running?
- Navigate to http://[Elk IP address]:5601/app/kibana to ensure the elk server is running.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
