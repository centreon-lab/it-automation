Ansible IT Automation
=====================

Ansible is a tool ....


Playbooks
=========

Playbook is a file contains ...

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
ansible-playbook centreon-poller.yaml
```


Centreon Web Playbook
--------------------

```
ansible-playbook centreon-poller.yaml
```

Example
=======

Complete example of implementation one enviorement with Centreon Web and two pollers
