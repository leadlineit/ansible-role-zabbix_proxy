# Ansible Role for Zabbix Proxy 5.4

![Build Status](https://github.com/leadlineit/ansible-role-zabbix_proxy/actions/workflows/ansible-galaxy-ci.yml/badge.svg)
[![Galaxy Role](https://img.shields.io/badge/Ansible--Galaxy-leadlineit.zabbix_proxy-blue.svg?logo=ansible&logoColor=white)](https://galaxy.ansible.com/leadlineit/zabbix_proxy/)

This role helps to install and configure Zabbix Proxy 5.4 to Debian (bullseye/buster).

Requirements
------------

This role requires Ansible 2.9 or higher.

Role Variables
--------------

```yaml
---
zabbix_proxy_dbname: zbx_proxy
zabbix_proxy_dbuser: zabbix
zabbix_proxy_dbpass: Aver@gEStr0ngPaSSw0rd
```

The next variables are optional, if you omit them the values below will be used (default).

```yaml
---
zabbix_proxy_mode: 0
zabbix_proxy_server: 127.0.0.1
zabbix_proxy_listen_port: 10051
zabbix_proxy_psk: 6c4ccf50bacdb3486f141ba1112e4a46  # openssl rand -hex 16/(32)
zabbix_proxy_psk_identity: localhost
```

Dependencies
------------

First, for this role you need to install MySQL Server 8.0.
You can do it yourself, or by using my dependency role.

```yaml
---
dependencies:
  - role: leadlineit.mysql_server
    tags: mysql_server
    vars:
      mysql_root_password: "{{ mysql_root_password | mandatory }}"
```

  *You can use default value for {{ mysql_root_password }} or your own.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: servers
  roles:
    - { role: leadlineit.zabbix_proxy, tags: zabbix_proxy }
```

License
-------

MIT

Author Information
------------------

This role was created by Artem Kasianchuk.
