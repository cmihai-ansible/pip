Role Name
=========

pip: Python pip module installer

[![Build Status](https://travis-ci.org/cmihai-ansible/pip.svg?branch=master)](https://travis-ci.org/cmihai-ansible/pip)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/crivetimihai/pip](https://galaxy.ansible.com/crivetimihai/pip)

```bash
ansible-galaxy install crivetimihai.pip
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
pip_packages_state: present
pip_remove_packages: true
pip_enable_service: true
pip_enable_selinux: true
pip_copy_templates: true
pip_firewall_configure: true
pip_firewall_rules:
  - service: ssh
  - port: 3389
pip_users:
  - user: devops
    group: docker
pip_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install pip on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: pip is configured
      import_role:
        name: crivetimihai.pip
      vars:
        pip_packages_state: present
        pip_remove_packages: true
        pip_enable_service: true
        pip_enable_selinux: true
        pip_copy_templates: true
        pip_firewall_configure: true
        pip_firewall_rules:
          - service: ssh
          - port: 3389
        pip_users:
          - user: devops
            group: docker
        pip_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: pip
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai/)
