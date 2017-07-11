Ansible Foreman [![Build Status](https://travis-ci.org/wilmardo/ansible-letsencrypt.svg?branch=master)](https://travis-ci.org/wilmardo/ansible-letsencrypt)
=========

Ansible role to enable Ansible management in Foreman with the foreman_ansible plugin:
https://theforeman.org/plugins/foreman_ansible/1.x/index.html

Requirements
------------
None

Role Variables
--------------
There are several role variables, they can be set in the hosts_vars or group_vars:

### Variables Ansible foreman

| Variable name                 | Default value                                     | Description         |
| -------------------------     | ---------------------                             | ------------------- |
| foreman_packages              | { python-request, tfm-rubygem-foreman_ansible }   | Default packages to install for Ansible Foreman to work
| foreman_ansible_cfg_location  | /etc/ansible/ansible.cfg                          | Location of the Ansible to edit, Ansible defaults to /etc/ansible/ansible.cfg [(docs)](http://docs.ansible.com/ansible/galaxy.html#roles-path) so best to leave it
| foreman_inventory_path        | /etc/ansible/hosts                                | The inventory_path [(docs)](http://docs.ansible.com/ansible/galaxy.html#inventory-path) to set in the ansible.cfg
| foreman_roles_path            | /etc/ansible/roles                                | The roles_path [(docs)](http://docs.ansible.com/ansible/galaxy.html#roles-path) to set in the ansible.cfg, multiple can be defined separated by a :
| foreman_system_variables      | Foreman defaults                                  | See [defaults/main.yml](defaults/main.yml) for the default values and an explanation. These values work with the defaults of the kostyrev.foreman role

Dependencies
------------
The foreman role of kostyrev:
https://galaxy.ansible.com/kostyrevaa/foreman/

Example Playbooks
----------------

### Example Playbook with defaults
The following playbook gives an example when using Apache and the autoinstall.

    - hosts: webservers    
      roles:
         - { role: wilmardo.foreman }

### Example Playbook with diffrent inventory path and multiple role paths
The following playbook gives an example when using Nginx with a webroot and a 4096 rsa_key_size

    - hosts: webservers    
      roles:
         - { role: wilmardo.foreman,    foreman_inventory_path: /home/user/ansible-project/hosts,
                                        foreman_roles_path: /home/user/ansible-project/roles:/home/user/ansible-project/galaxy-roles
License
-------

BSD

Author Information
------------------

Wilmar den Ouden

https://wilmardenouden.nl