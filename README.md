Ansible role for vProtect Node
=========

This ansible role installs Storware vProtect Node - data mover that executes backup tasks (nodes are managed by vProtect Server, provided in a separate role). Find out more here: https://storware.gitbook.io/storware-vprotect

Requirements
------------

Target host - CentOS/RHEL 7 minimal with root permissions. You also need running vProtect Server and provide variable `server_fqdn` so that nodes will be automatically registered

Role Variables
--------------

- `server_fqdn` - FQDN of the host where vProtect Server is working - it is expected to communicate over port 8181

Host variables:
- `node_name` - node name, if not provided hostname will be used; nodes must have unique names

Dependencies
------------

None

Example Playbook
----------------

Sample hosts inventory:

```
[all:vars]
ansible_user = root
server_fqdn = 192.168.1.2

[nodes]
192.168.1.3 node_name=node1
192.168.1.4 node_name=node2
```

Sample site.yml:

```
- hosts: nodes
  roles:
  - xe0nic.ansible_vprotect_node
```

License
-------

BSD

Author Information
------------------
