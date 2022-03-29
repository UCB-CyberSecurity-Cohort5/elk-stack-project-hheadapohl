# ELK-Stack-Project
Project 1 - ELK Stack Project

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Alt text](images/project1_network_diagram_HH.png?raw=true "Optional Title")

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the scripts folder may be used to install only certain pieces of it, such as Filebeat.

  - Install-elk.yml
  - filebeat-playbook.yml_
  - metricbeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly resilient and available, in addition to restricting unauthorized access to the network.
The load balancer ensures the availability portion of the CIA triad by sharing the incoming traffic among multiple identical web servers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file systems and system events, like attempted logins.
- Filebeat watches for changes in the file systems.
- Metricbeat looks for changes in system parameters like CPU usage, failed ssh logins, and failed SUDO attempts.

The configuration details of each machine may be found below.


| Name      | Function | IP Address | Operating System    |
|-----------|----------|------------|---------------------|
| Jump Box  | Gateway  | 10.0.0.4   | Linux (ubuntu 18.04)|
| ELK-SERVER| ELK Host | 10.1.0.4   | Linux (ubuntu 18.04)|
| Web-1     | DVWA Host| 10.0.0.5   | Linux (ubuntu 18.04)|
| Web-2     | DVWA Host| 10.0.0.6   | Linux (ubuntu 18.04)|
| Web3      | DVWA Host| 10.0.0.7   | Linux (ubuntu 18.04)|
### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the RedTeamLoadBalancer and ELK-SERVER machines can accept connections from the Internet. Access to this machine is only allowed from the following IP address:
- 8.3.82.213

Machines within the network can only be accessed by JumpBox (10.0.0.4) via a docker container running ansible.

A summary of the access policies in place can be found in the table below.

| Name          | Publicly Accessible | Allowed IP Addresses |
|---------------|---------------------|----------------------|
| Jump Box      | Yes                 |   8.3.82.213         |
| Load Balancer | Yes                 |   8.3.82.213         |
| ELK-SERVER    | Yes                 |   8.3.82.213         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows for reusability, reduces human error, and is more time efficient.

The playbook implements the following tasks:
```
---
- name: Configure Elk VM with Docker
  hosts: elk
  remote_user: RedAdmin
  become: true
  tasks:
    # Use apt module to install docker.io
    - name: Install docker.io
      apt:
        update_cache: yes
        force_apt_get: yes
        name: docker.io
        state: present

      # Use apt module to install python3 to use pip later
    - name: Install python3-pip
      apt:
        update_cache: yes
        force_apt_get: yes
        name: python3-pip
        state: present

      # Use pip module to install the python3 docker
    - name: Install Docker ELK module
      pip:
        name: docker
        state: present

      # Use sysctl to increase available memory
    - name: Increase virtual memory
      sysctl:
        name: vm.max_map_count
        value: '262144'
        state: present
        #have this memory expansion reload upon reboot
        reload: yes

      # Use docker_container module to install elk image
    - name: download and launch a docker elk container
      docker_container:
        name: elk
        image: sebp/elk:761
        state: started
        restart_policy: always
        # listing ports necessary for ELK
        published_ports:
          -  5601:5601
          -  9200:9200
          -  5044:5044

      # Use systemd module to ensure docker restarts on reboot
    - name: Enable service docker on boot
      systemd:
        name: docker
        enabled: yes
        
 ```
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Alt text](/images/Day1_Step3_check_elk_running.png?raw=true "Optional Title")

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1: 10.0.0.5
- Web-2: 10.0.0.6
- Web3: 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat
- metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat detects changes to the filesystem, while metricbeat detects changes in system events, such as CPU usage, failed SUDO attempts, ssh login attempts, and statistics such as RAM and CPU usage.

### Using the Beat Installation Playbooks
In order to use these playbooks, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
- Copy the install-elk.yml, filebeat-playbook.yml, and metricbeat-playbook.yml file to /etc/ansible/ in the ansible container. The easiest way to do this is to use git-clone and copy the files from this project's scripts directory.
- Modify the ansible hosts file to specify a separate group of VMs [elk] with the elk machine's internal IP (10.1.0.4).
- Update the filebeat-config.yml or metricbeat-config.yml files to include the proper host machine (10.1.0.4) under setup.kibana and output.elasticsearch. 
- Run the playbooks in succession using ansible-playbook, and navigate to 104.40.87.198:5601 to check that the installation worked as expected.

### For the step-by-step instructions, settings, and commands necessary for implementing this deployment, please visit associated document Step-by-step_commands.md


