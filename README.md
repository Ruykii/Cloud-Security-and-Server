## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](https://cdn.discordapp.com/attachments/792243138890694660/973243891358785556/unknown.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  - [Ansible Playbooks](https://github.com/Ruykii/MSUBootcamp2022/tree/main/Ansible)

This document contains the following details:
- Description of the Topologu
- Access Policies 
- [ELK Configuration](https://github.com/Ruykii/ELK-Stack-Cloud-Monitor-/blob/main/Ansible/pythonpentest.yml) 
  - Beats in Use
    - [Filebeat playbook](https://github.com/Ruykii/ELK-Stack-Cloud-Monitor-/blob/main/Ansible/filebeatplaybook.yml)
    - [Filebeat Config](https://github.com/Ruykii/ELK-Stack-Cloud-Monitor-/blob/main/Ansible/filebeat-conf.yml)
    - [Metricbeat playbook](https://github.com/Ruykii/ELK-Stack-Cloud-Monitor-/blob/main/Ansible/metricbeatplaybook.yml)
    - [Metricbeat config](https://github.com/Ruykii/ELK-Stack-Cloud-Monitor-/blob/main/Ansible/Metricbeat%20Config.yml)
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secured, in addition to restricting attacks to the network.
- The load balancer prevents certain attacks such as DDoS attacks. The Jump box allows 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
-  This filebeat is to collect and hold logs that are written through the local syslog serve of Unix based distributions. 
-  Metricbeat records of the operating system and services that are running on the Unix servers. 

The configuration details of each machine may be found below. 
[Virtual machine information](https://github.com/Ruykii/ELK-Stack-Cloud-Monitor-/tree/main/Azure/Virtual%20Machines)

| Name     | Function | IP Address | Operating System |
|----------|------------|----------|------------------|
| Jump Box | Gateway    | 10.0.0.1 | Linux            |
| Web 1    | Web Server | 10.0.0.8 | Linux            |
| Web 2    | Web Server | 10.0.0.9 | Linux            |
| ELK      | ELK server | 10.1.0.4 | Linux            |

### Access Policies
[Inbound rules for the machines](https://github.com/Ruykii/ELK-Stack-Cloud-Monitor-/tree/main/Azure/Inbound%20Security%20Group%20Rules)
The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Only whitelisted IP that the Jumpbox can connect through is the hosts's computer which is 174.102.170.50.

Machines within the network can only be accessed by the Jumpbox machine through a docker.
- Each machine can be accessed through the docker that is connected to the jumpbox. The jumpbox ip is 20.213.61.183. 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                 | 10.0.0.1, 10.0.0.2, 10.1.0.4 |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- Using ansible playbooks allow each downloads and configuration is running through each steps and if a step had a problem that involved within a certain point then troubleshooting becomes a lot easier to deal with. This allows me to also rerun through specific installation without multiple programs being downloaded if a certain program has already installed due to the nature of ansible playbooks.  

The playbook implements the following tasks:
- Download a container program, we used docker.io to create containers 
```
sudo apt install docker.io
    sudo systemctl status docker #This allows us to see if it is running.
        # If it is not running use: sudo systemctl start docker
```

- Then download a image using 'sudo docker pull'
- We downloaded specific containers from a docker hub using: 
```
  sudo docker pull cyberxsecurity/ubuntu:bionic
      sudo docker run -ti bionic/ubuntu bash #this will allow us to run it
```
- Now that we have created a container we can run ansible (by just writing ansible in to the command)
- We added our private ip's of our webservers in to hosts, and changed the remote_user in ansible.cfg to match the admin username. This is a must if we want to connect our      playbooks to our webservers. 



The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Docket output](https://cdn.discordapp.com/attachments/792243138890694660/973275317420564510/unknown.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-The ELK monitors the two web servers (web 1: 10.0.0.8, web 2: 10.0.0.9)

We have installed the following Beats on these machines:
- Filebeats
  [Proof of filebeats](https://github.com/Ruykii/ELK-Stack-Cloud-Monitor-/blob/main/screenshot%20and%20diagram/filebeatsuccess.PNG)
- Metricbeat
  [Proof of metricbeat](https://github.com/Ruykii/ELK-Stack-Cloud-Monitor-/blob/main/screenshot%20and%20diagram/metricbeatsusccess.PNG)

These Beats allow us to collect the following information from each machine:
- The beats allows us to see logs of what are written in the local syslong. As well as keeping a metric record of the operating system and services. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- We will add the ssh key-gen public key of our container to the ssh options for our webserver 1 and 2. This will allows us to connect our container. 
- There we add our configuration if needed or playbooks running nano and the name of playbook of config in to our /etc/ansible
- If all steps are met then you will be able to run ansible-playbook name.yml

    - Troubleshooting notes: 
    -
      - Make sure your virtual machines are on before running your playbooks. 
      - Check if you are using the write username and ip (must be private) in order for them to connect, if it does not match your information provided through your server then it will not run.
      - Adding the write terms for yaml file, playbook reads yaml and json files and will read it as json if you do not add the nesscary command in the beginning of the textfile.


- The playbook is provided in to our etc/ansible
- We can change the path of our playbooks by checking our hosts and ansible cfg as well as hosts name in our yaml
- If we want to see if our ELK is running our kibana we go to our browser and type in [public ip of elk]:5601/app/kibana
