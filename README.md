## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Network Diagram](https://github.com/WB-CARDOSO/ELK-Project/blob/main/Diagrams/Network%20Diagram.PNG)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the **YAML** file may be used to install only certain pieces of it, such as Filebeat.

[ELK Playbook](https://github.com/WB-CARDOSO/ELK-Project/blob/main/Ansible/ELK.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly **Available**, in addition to restricting **Access** to the network.

-What aspect of security do load balancers protect? **Availability**
-What is the advantage of a jump box? **Increases security by leaving only one entry point to a network**

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the **Operating System** and system **Logs**.

-What does Filebeat watch for? **Changes to protected files and logs**
-What does Metricbeat record? **Spikes in system resource usage**

The configuration details of each machine may be found below.

| NAME    | FUNCTION    | IP ADDRESS                | OPERATING SYSTEM |
|---------|-------------|---------------------------|------------------|
| JUMPBOX | ENTRY POINT | 10.1.0.4 / 20.85.217.20   | LINUX            |
| WEB-1   | BEATS       | 10.1.0.5                  | LINUX            |
| WEB-2   | BEATS       | 10.1.0.6                  | LINUX            |
| WEB-3   | BEATS       | 10.1.0.7                  | LINUX            |
| ELK-VM  | SIEM TOOL   | 10.0.0.4 / 104.42.179.154 | LINUX            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the **JUMPBOX** machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-Whitelisted IP: **99.252.148.109**

Machines within the network can only be accessed by **The JUMPBOX**.

-Which machine did you allow to access your ELK VM? **The JUMPBOX**.
-What was its IP address? **10.1.0.4**

A summary of the access policies in place can be found in the table below.

| NAME    | PUBLICALLY ACCESSIBLE | ALLOWED IP     |
|---------|-----------------------|----------------|
| JUMPBOX | YES                   | 99.252.148.109 |
| WEB-1   | NO                    | N/A            |
| WEB-2   | NO                    | N/A            |
| WEB-3   | NO                    | N/A            |
| ELK-VM  | YES                   | ANY            |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

-What is the main advantage of automating configuration with Ansible? **It can be automated and easily duplicated**

The playbook implements the following tasks:
- ... Install docker.io
- ... Install Python modules
- ... Increases memory to support ELK use
- ... Downloads and enables ELK container image
- ... Allows persistance for auto start upon reboot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![DockerPS](https://github.com/WB-CARDOSO/ELK-Project/blob/main/Diagrams/docker%20ps.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

| WEB-1   | BEATS       | 10.1.0.5                  | LINUX            |
| WEB-2   | BEATS       | 10.1.0.6                  | LINUX            |
| WEB-3   | BEATS       | 10.1.0.7                  | LINUX            |

We have installed the following Beats on these machines:

- **Filesbeat and Metricbeat**

These Beats allow us to collect the following information from each machine:

- Filebeat - **Collects log files and protected system files and monitors access and modification.**
- Metricbeat - **Monitors designated systems for resources use.**

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the **YAML** file to **/etc/ansible/files** directory.
- Update the **Hosts** file to include **Group of vms and their IP Addresses.**
- Run the playbook, and navigate to **Target VM** to check that the installation worked as expected.
- Which file is the playbook? **YAML**
- Where do you copy it? **/etc/ansible/files**
- Which file do you update to make Ansible run the playbook on a specific machine? **The desired playbook (YAML) file**
- How do I specify which machine to install the ELK server on versus which to install Filebeat on? **You need to write the group (webserver etc.) in the playbook files (YAML)**
- Which URL do you navigate to in order to check that the ELK server is running? **The ELK VM's public IP Address**

### DONE
