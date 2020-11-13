## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png) – 
Diagrams/Project 1 Network Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._
  -my_first_playbook.yml
  -install-elk.yml
  -filebeat-playbook.yml
  -metricbeat-playbook.yml

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
- _TODO: What aspect of security do load balancers protect? It helps protect against distributed denial-of-service (DDoS) attacks. What is the advantage of a jump box? It automatically blocks the public ip addresses assoicated with machines in the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file names and system metrics.
- _TODO: What does Filebeat watch for?_ Filebeat monitors for changes in the filesystem.
- _TODO: What does Metricbeat record?_ Metricbeat monitors for changes in system metrics such CPU usage or system login attempts.
 
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.


| Name        | Function      | IP Address | Operating System |
|-------------|---------------|------------|------------------|
| Jump-Box-VM | Gateway       | 10.1.0.4   | Linux            |
| Web-1       | Webserver     | 10.1.0.8   | Linux            |
| Web-2       | Webserver     | 10.1.0.6   | Linux            |
| Web-3       | Webserver     | 10.1.07    | Linux            |
| Elk-VM      | Logging       | 10.2.0.5   | Linux            |
|readteamlb   | Load balancer | 13.90.32.92| N/A              |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the readteamlb load balancer and Elk-VM machines can accept connections from the Internet. Access to these machines is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_ - 67.191.186.89

Machines within the network can only be accessed by Jump-Box-VM.
- _TODO: Which machine did you allow to access your ELK VM? My Workstation What was its IP address?_67.191.186.89

A summary of the access policies in place can be found in the table below.

| Name        | Publicly Accessible | Allowed IP Addresses    |
|-------------|---------------------|-------------------------|
| Jump-Box-VM | No                  | 67.191.186.89           |
| Web-1       | No                  | 10.1.0.4,10.2.0.5       |
| Web-2       | No                  | 10.1.0.4,10.2.0.5       |
| Web-3       | No                  | 10.1.0.4,10.2.0.5       |
| Elk-VM      | Yes                 | 67.191.186.89, 10.1.0.4 |
| readteamlb  | Yes                 | 67.191.186.89           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
It allows tasks to be completed quickly without the user remembering syntax.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install docker.io
- Install python3-pip
- Install docker module
- Increase virtual memory
- Download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)
Screenshot/Docker ps result.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_
- Web-1
- Web-2
- Web-3

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

-	Metricbeat is used to collect changes in the system metric data.    Metrics such as CPU and memory usage are used to track performance.

-	Filebeat is used to collect logs for changes to the system.  It can collect information such as SSH login attempts to track users logging into the system and if it failed or was successful. 


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? 
  -my_first_playbook.yml
  -install-elk.yml
  -filebeat-playbook.yml
  -metricbeat-playbook.yml
Where do you copy it?_
Copy it to the /etc/ansible directory
- _Which file do you update to make Ansible run the playbook on a specific machine? 
The hosts file located in /etc/ansible. 
How do I specify which machine to install the ELK server on versus which to install Filebeat on?
In the install-elk.yml file, update the hosts with the name of the elk server group entered in the ansible hosts file. 
In the filebeat-playbook.yml file, update the hosts with the name of the server group entered in the ansible hosts file.
- _Which URL do you navigate to in order to check that the ELK server is running? http://40.123.51.91:5601/app/kibana#

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
