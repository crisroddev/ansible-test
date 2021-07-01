########################################################################
################EXCELIRATE DEVOPS TECNICAL TEST#########################
################CRISTIAN RODRIGUEZ ALBAGLI##############################
################cristian@crisrodalbagli.com#############################
########################################################################

# Xcelirate Tecnical test

_This is my tecnical test for the lead Devops position_

## Starting 🚀

_Next we have al the instructions to deploy the virtual machines and ansible to install redis, mysql and rabbitmq_

### Pre-requisits 📋

_You need to do the following steps to run vagrant and install VMs_
_In folder xcelirate_

```
vagrant up
```

### Running and Configuration of ansible 🔧

_You need to do some steps_

_Create known host connection and run asnible playbooks_

```
vagrant ssh setup
ssh vagrant@192.168.33.11

```

_Accept connection and write password_

```
Accept: yes
Password: vagrant

```

_Run Ansible Playbook_
```
ansible-playbook -i hosts.yaml playbook.yaml

```

### More Information ⌨️

_With the steps above you will deploy Redis, MySQL, and RabbitMQ Containers_

* **Redis** - *Validations*
```
sudo docker exec -it redis-container sh
redis-cli -a root
set name xcelirate
get name
```
* **MySQL** - *Validations*
```
sudo docker exec -it mysql-container bash
mysql -uroot -p
use xcelirate
```
* **RabbitMQ** - *Validations*
```
Web Browser: 192.168.33.11:15672
user: rabbitmq
password: rabbitmq
```

## Build It With  🛠️

_Tools used for this project_

* [Vagrant](https://www.vagrantup.com/docs) - Creation and Set Up of VMs
* [Ansible](https://docs.ansible.com/) - Project Automation
* [Docker](https://docs.docker.com/) - Automate application deployment within software containers
* [Ansible Galaxy](https://docs.ansible.com/ansible/latest/cli/ansible-galaxy.html/) - Repository for Ansible Roles

## Author

* **Cristián Rodriguez** - [crisroddev](https://github.com/crisroddev)