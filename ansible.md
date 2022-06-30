# Ansible
- Ansible can actually do both orchestration and management - but we also learn Terraform because some companies use it.
- Agentless - because everything you need to install only needs to be installed on Ansible. The other server does not need to have Ansible installed.
- It uses SSH protocol to connect the servers. Ansible requires Python to make the use of modules on client machines
- Ansible uses Yaml files to configure/ provision servers. A provisioning.sh script can do multiple things in one server only. But with Ansible, the yaml scripts can have numerous instructions for multiple servers.

## Ansible playbook vs bash script
- Bash (or another scripting language) describes actions. Do this thing. Now do this other thing.

- Ansible (and other configuration management systems) describe the desired state. This file should exist here, owned by this user, with these permissions. This package should be installed. This line in this config file should appear like this.

## Ansible controller setup
- `sudo apt-get install software-properties-common`
- `sudo apt-add-repository ppa:ansible/ansible`
- `sudo apt-get update -y`
- `sudo apt-get install ansible -y`
- to ssh into other servers from the controller `ssh NameOfServer@ServerIP` eg. ssh ubuntu@192.168.33.11

## Ansible directory structure
- cd /etc/ansible
- ls -> when we do ls we have 3 objects in the ansible folder `ansible.cfg` `hosts` `roles`
- in the `hosts` file enter the other servers' ip addresses so that they are connected 
- in the host file create a group for the `app` and one for the `db`
```bash
[web]
192.168.33.10 ansible_connection=ssh ansible_ssh_user=vagrant ansible_ssh_pass=vagrant
[db]
192.168.33.11 ansible_connection=ssh ansible_ssh_user=vagrant ansible_ssh_pass=vagrant
```
### ansible Ad Hoc command
Ad Hoc commands are commands that are run in the ansible controller to get information from the nodes without ssh in
- to find information about machine - `ansible web -a "uname -a"` (-a stands for arguement | -m stands for module)
- Check the connection to these other VMs `ansible web -m ping`
  - You should see `Ping: Pong`
- to check connectivity for all `ansible all -m ping`
- Run commands on the other VMs from controller VM: `ansible web -a "command"`
   - eg. `ansible web -a "uptime"`
- amount of free space `ansible all -a "free"`
- `ansible all -a "sudo apt-get install tree -y"` the command will run it on the nodes but we are running it on controller
- `ansible web -a "pwd"` working directory of web
- transfer file to nodes `ansible all -m copy -a "src=/etc/ansible/test.txt dest=/home/ubuntu"`

