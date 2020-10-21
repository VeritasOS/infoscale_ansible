# InfoScale Ansible Examples
This repository contains examples of playbooks to accompany my Veritas VOX blog post on deploying InfoScale with Ansible. You can find that blog post here: <blog post link>
## Howto
The playbooks are divided into two parts. The first part, vmware_ansible contains playbooks showing how I prepared the virtual machines in my lab for InfoScale installation.

The second part, infoscale_ansible contains playbooks showing how I installed InfoScale and configured a Clustered File System. 

# vmware_ansible Playbook
This is an example playbook I use for cloning and deploying VMware Virtual Machines. 

## Notes
The playbook is organized to make it easier to manage tasks. Look in the roles/vmware/tasks directory to find the operations I use in this example.

The file group_vars/vars should be encrypted as it will require your vsphere credentials. See these instructions: https://docs.ansible.com/ansible/2.4/ansible-vault.html 

## Usage
``` ansible-playbook site.yml --ask-vault-pass```

# infoScale_ansible Playbook
This is an example InfoScale Ansible Playbook.

## Notes
This playbook is divided into two parts. The first, roles/common performs the instaallation of pre-requisites required for InfoScale. The second, roles/infoscale contains InfoScale related tasks such as installing InfoScale software, configuring InfoScale, etc. 

For more information and official documentation, please see the following web page: https://sort.veritas.com/utility/ansible

## Usage
### Installing Pre-requisites
```ansible-playbook pre_infoscale.yml```

This playbook performs the following tasks:
* Configure local RHEL repos
* Update the OS. At the time of the writing of this playbook, the dnf module didn't support the ```--nobest``` flag, thus the command modules was used.
* Install python2
* Install the netaddr python2 module
* Add the /opt/VRTS/bin to the path.
* Set the default kernel to 147.
* Add host entries for all the InfoScale nodes in the primary and secondary clusters.

### Installing InfoScale
```ansible-playbook infoscale_install.yml```

### Configuring InfoScale
```ansible-playbook infoscale_configure.yml```

### Create Disk Groups and Volumes
```ansible-playbook infoscale_dg_create.yml```

### Create Cluster File System
```ansible-playbook infoscale_cfs_create.yml```

#
Copyright <YEAR> <COPYRIGHT HOLDER>
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
