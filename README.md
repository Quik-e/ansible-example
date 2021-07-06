# Ansible Example
This repository shows a simulation to deploy an infrastructure configuration using Ansible. Every host is a container based on Ubuntu image Focal Fossa from DockerHub. Ansible was installed on one of these servers. This deployment was tested on a Raspberry Pi 3B.
Once Ansible is used, the network will be formed by:
- 3 WebServers, running NGINX.
- 1 DBServer, running MariaDB.
- 1 FileServer, running Samba.
- 3 Workstations for the DevTeam, with their Text Editor of choice (Vim, Emacs, Nano).

## Environment Deployment
In the root folder of the repo you run:
```sh
$ docker-compose up -d
```
If the deployment is too much simultaneous workload for your computer, you can run the script:
```sh
$ ./start.sh
```

## Using SSH Keys with ansible
Once deployed, you must connect through ssh and run the script to prepare all containers for correct Ansible management. The servers will have an ansible user with a nopassphrase SSH key and a sysadmin user with an SSH key with passhphrase. Root login through ssh will also be disabled and both ansible and sysadmin users will be sudoers. 

```sh
$ ssh root@192.168.1.210
# cd /etc/ansible
# ansible-playbook -i new_hosts no_pass_ssh.yml
```

## Configure each host
Programs will be installed on all hosts. New users will be added to each of the Workstations.
```sh
# annsible-playbook prepare_infrastructure.yml
```
