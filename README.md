Role Name
=========

solr: Solr

[![Build Status](https://travis-ci.org/cmihai-ansible/solr.svg?branch=master)](https://travis-ci.org/cmihai-ansible/solr)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.solr](https://galaxy.ansible.com/devopstoolbox.solr)

```bash
ansible-galaxy install devopstoolbox.solr
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
solr_packages_state: present
solr_remove_packages: true
solr_enable_service: true
solr_enable_selinux: true
solr_copy_templates: true
solr_firewall_configure: true
solr_firewall_rules:
  - service: ssh
  - port: 3389
solr_users:
  - user: devops
    group: docker
solr_selinux_booleans:
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
- name: Install solr on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: solr is configured
      import_role:
        name: devopstoolbox.solr
      vars:
        solr_packages_state: present
        solr_remove_packages: true
        solr_enable_service: true
        solr_enable_selinux: true
        solr_copy_templates: true
        solr_firewall_configure: true
        solr_firewall_rules:
          - service: ssh
          - port: 3389
        solr_users:
          - user: devops
            group: docker
        solr_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: solr
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
