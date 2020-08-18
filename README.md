# RedHat-Ansible-Training

## [Introduction to Ansible]

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


## [Ansible Architecture]

Ansible works by connecting to your nodes and pushing out small programs, called "Ansible modules" to them. These programs are written to be resource models of the desired state of the system. Ansible then executes these modules (over SSH by default), and removes them when finished.

![Ansible architecture](https://github.com/srabhayraj/RedHat-Ansible-Training/blob/master/metadata/images/ansible-architecture.png)


## [Ansible Deployment]

Ansible is the simplest way to deploy your applications. It gives you the power to deploy multi-tier applications reliably and consistently, all from one common framework. You can configure needed services as well as push application artifacts from one common system.

![Ansible deployment](https://github.com/srabhayraj/RedHat-Ansible-Training/blob/master/metadata/images/ansible-deployment.jpg)


## [Ansible Inventory]

Ansible works against multiple systems in your infrastructure at the same time. It does this by selecting portions of systems listed in Ansible’s inventory file, which defaults to being saved in the location /etc/ansible/hosts. You can specify a different inventory file using the -i <path> option on the command line.
The Ansible inventory file defines the hosts and groups of hosts upon which commands, modules, and tasks in a playbook operate. The file can be in one of many formats depending on your Ansible environment and plugins. If necessary, you can also create project-specific inventory files in alternate locations.

![Ansible inventory](https://github.com/srabhayraj/RedHat-Ansible-Training/blob/master/metadata/images/ansible-inventory.jpg)



## [Installing Ansible]

Installing Ansible on RHEL, CentOS, or Fedora
On Fedora:
```
$ sudo dnf install ansible
```
On RHEL and CentOS:
```
$ sudo yum install ansible
```
RPMs for RHEL 7 and RHEL 8 are available from the Ansible Engine repository.

To enable the Ansible Engine repository for RHEL 8, run the following command:
```
$ sudo subscription-manager repos --enable ansible-2.9-for-rhel-8-x86_64-rpms
```
To enable the Ansible Engine repository for RHEL 7, run the following command:
```
$ sudo subscription-manager repos --enable rhel-7-server-ansible-2.9-rpms
```
RPMs for currently supported versions of RHEL, CentOS, and Fedora are available from EPEL as well as releases.ansible.com.

Ansible version 2.4 and later can manage earlier operating systems that contain Python 2.6 or higher.

You can also build an RPM yourself. From the root of a checkout or tarball, use the make rpm command to build an RPM you can distribute and install.

```
$ git clone https://github.com/ansible/ansible.git
$ cd ./ansible
$ make rpm
$ sudo rpm -Uvh ./rpm-build/ansible-*.noarch.rpm
```

