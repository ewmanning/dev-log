### Ansible

### Using LXC for testing Ansible

#### LXC Install

sudo apt-get update && apt-get install lxc

sudo apt-get install lxc-templates

#### Create LXC Container

sudo lxc-create -t ubuntu -n db1

#### Start LXC Container

lxc-start -n db1 -d

#### Setup SSH

ssh-agent /bin/bash

ssh-add ~/.ssh/id_rsa

#### Ansible Configuration

less /etc/ansible/ansible.cfg
