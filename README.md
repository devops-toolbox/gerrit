Role Name
=========

gerrit: Gerrit

[![Build Status](https://travis-ci.org/cmihai-ansible/gerrit.svg?branch=master)](https://travis-ci.org/cmihai-ansible/gerrit)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.gerrit](https://galaxy.ansible.com/devops-toolbox.gerrit)

```bash
ansible-galaxy install devops-toolbox.gerrit
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
gerrit_packages_state: present
gerrit_remove_packages: true
gerrit_enable_service: true
gerrit_enable_selinux: true
gerrit_copy_templates: true
gerrit_firewall_configure: true
gerrit_firewall_rules:
  - service: ssh
  - port: 3389
gerrit_users:
  - user: devops
    group: docker
gerrit_selinux_booleans:
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
- name: Install gerrit on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: gerrit is configured
      import_role:
        name: devops-toolbox.gerrit
      vars:
        gerrit_packages_state: present
        gerrit_remove_packages: true
        gerrit_enable_service: true
        gerrit_enable_selinux: true
        gerrit_copy_templates: true
        gerrit_firewall_configure: true
        gerrit_firewall_rules:
          - service: ssh
          - port: 3389
        gerrit_users:
          - user: devops
            group: docker
        gerrit_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: gerrit
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
