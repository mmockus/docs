---
sidebar_position: 12
---

# Ansible

## Overview

## Installation

```bash
sudo apt update
sudo apt install software-properties-common # for add-apt-repository
apt install ansible
# optional install sshpass
sudo apt install sshpass
```
## Configuration

- Create an inventory directory

- Create a module directory

- create an ansible.cfg

```yaml
[defaults]
interpreter_python = auto_silent
inventory = ./inventory/hosts

## Usage 

if you use ask pass, otherwise you can omit --ask-pass

```bash
ansible -1 ./inventory/hosts pi -m ping --user your-user --ask-pass
```

```bash
ansible-playbook ./playbooks/apt.yaml --user your-user --ask-become-pass -i ./inventory/hosts
```

Use the configured inventory file to run the playbook and limit the hosts to which the playbook is applied.
```bash
ansible-playbook ./playbooks/apt.yaml --user your-user --ask-become-pass --limit pi
```

![TODO](https://img.shields.io/badge/TO-DO-blue)  Setup templates

```bash
ansible-playbook ./playbooks/tempfile.yaml --user your-user --ask-become-pass --limit pi
```

## Tips

### Warning 1

- interprator_python = auto_silent makes this go away

```
[WARNING]: Platform linux on host mockus-pi-0 is using the discovered Python interpreter at /usr/bin/python, but future installation of another
Python interpreter could change this. See https://docs.ansible.com/ansible/2.9/reference_appendices/interpreter_discovery.html for more
information.
```

## Reference

Techno-tim: Automated Deployments with Ansible
<https://techno-tim.github.io/posts/ansible-automation/>

## License

[TODO]: https://img.shields.io/badge/TO-DO-blue