## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(diagrams/VirtualDiagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.


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

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network and system logs.


The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Server   | 10.0.0.5   | Linux            |
| Web-2    | Server   | 10.0.0.6   | Linux            |
| Web-3    | Server   | 10.0.0.8   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 75.83.27.32

Machines within the network can only be accessed by jumpbox (10.0.0.4).


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 75.83.27.32          |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because these same configurations
can easily be implemented on other machines if were to add them.

The playbook implements the following tasks:
- install docker
- install python
- install docker container
- enable docker service on server bootup

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/docker_ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6
- 10.0.0.8

We have installed the following Beats on these machines:
- metricbeat
- filebeat
These Beats allow us to collect the following information from each machine:
- Filebeat monitors the webservers and the logs to see if there are any changes to the server. Example: 2022-03-21T02:27:54.886Z#011INFO#011[monitoring]#011log/log.go:145#011Non-zero metrics in the last 30s#011{"monitoring": {"metrics": {"beat":{"cpu":{"system":{"ticks":800},"total":{"ticks":2770,"time":{"ms":11},"value":2770},"user":{"ticks":1970,"time":{"ms":11}}},"handles":{"limit":{"hard":524288,"soft":1024},"open":8},"info":{"ephemeral_id":"5b606e88-e6db-40c7-a04a-601e93fc7053","uptime":{"ms":5522978}},"memstats":{"gc_next":9258512,"memory_alloc":7498392,"memory_total":199278888},"runtime":{"goroutines":108}},"filebeat":{"events":{"added":2,"done":2},"harvester":{"open_files":1,"running":1}},"libbeat":{"config":{"module":{"running":0}},"output":{"events":{"acked":2,"batches":2,"total":2},"read":{"bytes":688},"write":{"bytes":4501}},"pipeline":{"clients":15,"events":{"active":0,"published":2,"total":2},"queue":{"acked":2}}},"registrar":{"states":{"current":3,"update":2},"writes":{"success":2,"total":2}},"system":{"load":{"1":0,"15":0,"5":0,"norm":{"1":0,"15":0,"5":0}}}}}}
- Metricbeat monitors the metrics and statistics of the webservers. We would see things like CPU usage, memory usage, etc.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible/files.
- Update the hosts file to include the elk server.
- Run the playbook, and navigate to 20.230.14.191 to check that the installation worked as expected.


