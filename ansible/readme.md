Ansible IT Automation
=====================

Ansible is an open source software that automates software provisioning, configuration management, and application deployment. Ansible connects via SSH.

See more information: https://docs.ansible.com/ansible/latest/index.html

Playbooks
=========

Playbooks express configurations, deployment, and orchestration in Ansible. The Playbook format is YAML. Each Playbook maps a group of hosts to a set of roles. Each role is represented by calls to Ansible tasks.

See more information: https://docs.ansible.com/ansible/latest/user_guide/playbooks.html

Centreon Poller Playbook
------------------------

Compatible:

* CentOS 6
* CentOS 7

Tasks:

* Disable selinux
* Add Centreon Open Source repository
* Import keys from repository
* Install packages to Centreon poller
* Set authorized previously created keys
* Enable and try start centengine service

```
ansible-playbook -i hosts centreon-poller.yaml
```


Centreon Web Playbook with MySQL Server
---------------------------------------

Compatible:

* CentOS 6
* CentOS 7

Tasks:

* Disable selinux
* Add Centreon Open Source repository
* Import keys from repository
* Install packages to Centreon poller
* Setup timezone to PHP
* Set custom option to Mysql in CentOS 7
* Generate SSH key (used by remote Centreon Poller)
* Start and enable services necessaries
* Setup firewall rules


```
ansible-playbook -i hosts centreon-web-with-mysqld.yaml
```

Example
=======

Complete example of implementation one environment with Centreon Web and two pollers

The `hosts` file with the nodes:

```
[centreon-poller]
172.20.0.11
172.20.0.12

[centreon-web]
172.20.0.100
```

Set group name of hosts in each playbook, change the first key `hosts` in file.

Create a file with the playbooks (eg: `deploy.yaml`) with content bellow:
```yaml
---
- import_playbook: centreon-poller.yaml
- import_playbook: centreon-web-with-mysqld.yaml
```

Run the deployment with command:
```
ansible-playbook -i hosts deploy.yaml
```
