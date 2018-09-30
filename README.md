Ansible-Deploy-User
=========

This ansible role creates a user with passwordless sudo & ssh login and disallows root ssh access. 

Boilerplate for an ansible managed server. 

Requirements
------------

A (new) Ubuntu server. 

Apply this role onto your new Ubuntu server to manage it with ansible. You need the IP address and the root password, obviously. 

It has been tested on Ubuntu 14.10, 16.04 & 18.04 but will probably work on most other Linux distribution.

Installation
------------
    $ ansible-galaxy install cbuggle.ansible_deploy_user


Usage / Example Playbook
----------------

Include this role in your `site.yml` 

    - name: "Setup ansible boilerplate" 
      hosts: all
      roles:
         - { role: cbuggle.ansible_deploy_user }

and run it in your terminal as an ansible-playbook.

    $ ansible-playbook -i inventory/hosts site.yml --user root --ask-pass


Role Variables
--------------

The behavior can be configured by overriding the defaults of these variables:

    ansible_user_name:          "ansible_deploy"
    user_shell:                 "/bin/bash"
    local_ssh_pub_key_path:     "~/.ssh/id_rsa.pub"

This can be done e.g. in a file named `vars/main.yml`.

If unsure how to do this please consult the general [Ansible Docs](https://docs.ansible.com/). 


Creating generic users?
---------------------
The sole purpose of this role is to create a user suitable for ansible deploys. Passwordless sudo & ssh login cannot be disabled.

A better tool to create customizable users instead might be [nickjj.ansible-user](https://github.com/nickjj/ansible-user) or check out [Ansible Galaxy](https://galaxy.ansible.com) 


License
-------

MIT
