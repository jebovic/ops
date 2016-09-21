# Ansible

## Theory

1. It Automation
2. Python
3. Agentless
4. Idempotent
5. Easy as YAML
6. Install, configure, deploy, orchestrate
7. Demo Time !

## Demo #1 : basics

### Inventory

1. Hosts
2. Groups
3. Variables

### ping

```
ansible -i inventories/local all -m ping
ansible -i inventories/local webservers -m ping
ansible -i inventories/local weblemp.local -m ping
```

### command

```
ansible -i inventories/local all -m command -a "cat /etc/os-release"
ansible -i inventories/local webservers -m command -a "cat /etc/os-release"
ansible -i inventories/local weblemp.local -m command -a "cat /etc/os-release"
```

### setup

```
ansible -i inventories/local weblemp.local -m setup
```

## Demo #2 : playbooks

1. Inventory
2. Variables
3. Roles
4. Playbook: roles orchestration

### rocket launch

```
ansible-playbook -i inventories/local webservers.yml --limit weblemp.local --ask-vault-pass
ansible-playbook -i inventories/local goservers.yml --limit golang.local --ask-vault-pass
```
