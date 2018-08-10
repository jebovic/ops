Ops: Build dev environment with Vagrant & Ansible
=================================================

Steps to get your environment up:

1. clone this repo
2. use vagrant with virtualbox provider to get your VM up
3. use ansible for VM provisioning

## Compatibility

Tested and approved on :

* Debian jessie (8+)
* Ubuntu Trusty (14.04 LTS)
* Ubuntu Xenial (16.04 LTS)

## Vagrant : Create a Virtual Machine

### Install Vagrant

All you need is to install [Vagrant](https://www.vagrantup.com/docs/installation).

### Run a Virtual Machine

Vagrant configuration (for virtualbox provider only) is present in the Vagrantfile, in the repository root.

Create and up a VM from a simple command (see Vagrantfile for the full list):

```
vagrant up [golang,ci,weblemp,weblamp,docker,monitoring...]
```

## Ansible: Virtual Machine provisioning

### Install ansible

The first step is to get ansible, i'd recomand to [get it from the source](http://docs.ansible.com/ansible/intro_installation.html#running-from-source) to be compatible with all the roles in the different playboks (ansible >= 2.2 required).

### Test your setup : ping

```
ansible -i inventories/local all -m ping
ansible -i inventories/local webservers -m ping
ansible -i inventories/local weblemp.local -m ping
```

### Test your setup : command

```
ansible -i inventories/local all -m command -a "cat /etc/os-release"
ansible -i inventories/local webservers -m command -a "cat /etc/os-release"
ansible -i inventories/local weblemp.local -m command -a "cat /etc/os-release"
```

### Test your setup : setup

```
ansible -i inventories/local weblemp.local -m setup
```

### Install roles from Ansible Galaxy

Install roles into the roles directory:

```
# install all roles from the requirements file to the playbooks/roles directory
cd playbooks/requirements
ansible-galaxy install -r all.yml -p ../roles
```

Alternatively, you can install only the desired roles from other requirements files:

```
# install only roles needed for the base playbook
cd playbooks/requirements
ansible-galaxy install -r base.yml -p ../roles

# Then you can add roles from a more specific playbook
ansible-galaxy install -r monitoring.yml -p ../roles
```

**My ansible roles**

* Ansible galaxy: [https://galaxy.ansible.com/jebovic](https://galaxy.ansible.com/jebovic/)
* Github: [https://github.com/jebovic](https://github.com/jebovic?utf8=%E2%9C%93&tab=repositories&q=ansible-&type=&language=)

### Run a playbook

**Example #1**: run the base playbook on all servers listed in ansible/_inventory file

```
cd ansible
ansible-playbook base.yml --ask-vault-pass
```

Note: don't forget to replace variables values from group_vars and host_vars, and replace encrypted values in ansible/group_vars/all/vault.yml with yours.

**Example #2**: run the webservers playbook against VM listed into the webservers group of the inventory

```
cd ansible
ansible-playbook nodes.yml --limit nodes
```

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic

