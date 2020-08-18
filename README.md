# RedHat-Ansible-Training

# [Introduction to Ansible]

◻ Ansible is simple open source IT engine which automates application deployment, intra service orchestration, cloud provisioning and many other IT tools.

◻ Ansible is easy to deploy because it does not use any agents or custom security infrastructure.

◻ Ansible uses playbook to describe automation jobs, and playbook uses very simple language i.e. YAML (It’s a human-readable data serialization language & is commonly used for configuration files, but could be used in many applications where data is being stored)which is very easy for humans to understand, read and write. Hence the advantage is that even the IT infrastructure support guys can read and understand the playbook and debug if needed (YAML – It is in human readable form).

◻ Ansible is designed for multi-tier deployment. Ansible does not manage one system at time, it models IT infrastructure by describing all of your systems are interrelated. Ansible is completely agentless which means Ansible works by connecting your nodes through ssh(by default). But if you want other method for connection like Kerberos, Ansible gives that option to you.

### How Ansible Works?
The picture given below shows the working of Ansible.

Ansible works by connecting to your nodes and pushing out small programs, called "Ansible modules" to them. Ansible then executes these modules (over SSH by default), and removes them when finished. Your library of modules can reside on any machine, and there are no servers, daemons, or databases required.

![Ansible works](https://github.com/srabhayraj/RedHat-Ansible-Training/blob/master/metadata/images/ansible_works.jpg)

The management node in the above picture is the controlling node (managing node) which controls the entire execution of the playbook. It’s the node from which you are running the installation. The inventory file provides the list of hosts where the Ansible modules needs to be run and the management node does a SSH connection and executes the small modules on the hosts machine and installs the product/software.

Beauty of Ansible is that it removes the modules once those are installed so effectively it connects to host machine , executes the instructions and if it’s successfully installed removes the code which was copied on the host machine which was executed.


## Ansible Architecture

Ansible works by connecting to your nodes and pushing out small programs, called "Ansible modules" to them. These programs are written to be resource models of the desired state of the system. Ansible then executes these modules (over SSH by default), and removes them when finished.

![Ansible architecture](https://github.com/srabhayraj/RedHat-Ansible-Training/blob/master/metadata/images/ansible-architecture.png)


## Ansible Deployment

Ansible is the simplest way to deploy your applications. It gives you the power to deploy multi-tier applications reliably and consistently, all from one common framework. You can configure needed services as well as push application artifacts from one common system.

![Ansible deployment](https://github.com/srabhayraj/RedHat-Ansible-Training/blob/master/metadata/images/ansible-deployment.jpg)


## Ansible Inventory

Ansible works against multiple systems in your infrastructure at the same time. It does this by selecting portions of systems listed in Ansible’s inventory file, which defaults to being saved in the location /etc/ansible/hosts. You can specify a different inventory file using the -i <path> option on the command line.
The Ansible inventory file defines the hosts and groups of hosts upon which commands, modules, and tasks in a playbook operate. The file can be in one of many formats depending on your Ansible environment and plugins. If necessary, you can also create project-specific inventory files in alternate locations.

![Ansible inventory](https://github.com/srabhayraj/RedHat-Ansible-Training/blob/master/metadata/images/ansible-inventory.jpg)


# [Deploying Ansible]

## [Installing Ansible]

Verify that the prerequisite version of Python is installed on workstation.
```
[student@workstation ~]$ yum list installed python
```
 Install Ansible on workstation so that it can serve the role of the control node.
 ```
[student@workstation ~]$ sudo yum install -y ansible
```
Verify that you can establish an SSH connection from workstation to servera to ensure that Ansible will be able to connect from the control node to the managed host using SSH.
Exit the SSH session after the verification is complete.
```
[student@workstation ~]$ ssh servera.lab.example.com
```
Warning: Permanently added 'servera.lab.example.com,172.25.250.10' (ECDSA) to the
list of known hosts.
```
[student@servera ~]$ exit
```
On the control node, create an inventory file, /home/student/dep-install/inventory, which contains a group called dev made up of a single managed host, servera.lab.example.com.
  1. Create and change directory to the /home/student/dep-install directory.
```
[student@workstation ~]$ mkdir /home/student/dep-install
[student@workstation ~]$ cd /home/student/dep-install
```
  2. Create the inventory file and add the following entries to the file to create the dev hostgroup and its single member (servera.lab.example.com).[dev] servera.lab.example.com
Execute the ansible command with the -i option to use the newly created inventory file and use the --list-hosts option to verify that the dev host group resolves to its single member, servera.
```
[student@workstation dep-install]$ ansible dev -i inventory --list-hosts
```
hosts (1):
servera.lab.example.com

You can also build an RPM yourself. From the root of a checkout or tarball, use the make rpm command to build an RPM you can distribute and install.

```
$ git clone https://github.com/ansible/ansible.git
$ cd ./ansible
$ make rpm
$ sudo rpm -Uvh ./rpm-build/ansible-*.noarch.rpm
```

