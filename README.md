### Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

<img width="462" alt="image" src="https://user-images.githubusercontent.com/99371844/153979007-04d6b972-0cee-4606-ad77-2400c90a779a.png">

These files have been tested and used to generate a live ELK deployment on Azure.They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook (.yml) file may be used to install only certain pieces of it, such as Filebeat.

Playbook file: /etc/ansible/install-elk-playbook.yml

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

What aspect of security do load balancers protect? 
- Load balancers protects the system from DDoS attacks by shifting attack traffic.
- Load Balancing contributes to the Availability aspect of security regarding the CIA Triad.


What is the advantage of a jump box?

-	The benefit of a jump box is to give access to the user from a single node that can be secured and monitored.
-	The advantage of a Jump Box is the origination point for launching Administrative Tasks.This ultimately sets the Jump Box as a Secure Admin Workstation. All    Administrators when conducting any Administrative Task will be required to connect to the jump box before preforming any assignment.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logfiles and system performance.

What does Filebeat watch for?
-	Filebeat observes for any information in the file system which has been changed and when the change occurs
-	Filebeat observes for log files, locations and collects log events


What does Metricbeat record?

-	Metricbeat takes the metrics and statistics that collects and transports them to the output specified.
-	Metricbeat records metric and statistical data from the operating system and from services running on the server.


The configuration details of each machine may be found below: 

| Name     | Function    | IP Address | Operating System |
|----------|-------------|------------|------------------|
| Jump Box | Gateway     | 10.0.0.4   | Linux            |
| Web-01   | Server      | 10.0.0.5   | Linux            |
| Web-02   | Server      | 10.0.0.6   | Linux            |
| Web-03   | Server      | 10.0.0.7   | Linux            |
| Elk-VM   | Elk Server  | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Add whitelisted IP addresses:- Public IP address which changes every time when the VM is on/off: Public IP 23.99.250.176

Machines within the network can only be accessed by SSH Port 22.

Which machine did you allow to access your ELK VM? What was its IP address?

- The ELK-Server is only accessible by SSH from the JumpBox and through web access from Personal IP Address.

| Name     | Publicly Accessible   | Allowed IP Addresses                             | 
|----------|-----------------------|--------------------------------------------------|
| Jump Box | Yes Via SSH           | 10.0.0.4                                         |
| Web-01   | Yes Thru Load Balancer| 168.61.182.25(Red-Team-LB) 10.0.0.5              |                              
| Web-02   | Yes Thru Load Balancer| 168.61.182.25(Red-Team-LB) 10.0.0.5              |                                          
| Web-03   | Yes Thru Load Balancer| 168.61.182.25(Red-Team-LB) 10.0.0.5.             |                                                      
| Elk-VM   | NO                    | SSH 10.1.0.4-JumpBox HTTP Port 5601 Personal IP  |
                                  

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
What is the main advantage of automating configuration with Ansible?
- The advantage of automating the configuration process is that this process makes it easy to deploy to multiple servers quickly without having to physically touch individual servers.

The playbook implements the following tasks:

-	Install Docker.io and python pip3
-	Install Docker
-	Command: sysctl -w vm.max_map_count=262144
-	Launch docker container: elk

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![image](https://user-images.githubusercontent.com/99371844/153986156-90ad3bb7-be32-460c-9689-984bded5aad7.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring.

-	Web-1	IP Address 10.0.0.5
-	Web-2	IP Address 10.0.0.6

We have installed the following Beats on these machines:
Specify which Beats you successfully installed

-	Filebeat
-	Metricbeat

These Beats allow us to collect the following information from each machine:
-	Filebeat monitors log files or specific locations, collects log   events, and forwards them either to Elasticsearch or Logstash for indexing.
-	Metricbeat collects metrics from the operating system and from services running on the server.


