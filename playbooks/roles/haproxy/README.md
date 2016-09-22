HAProxy
=======

Install and configure HAProxy

Role Variables
--------------

```
# Global configuration
haproxy_config_file: /etc/haproxy/haproxy.cfg

# UI configuration
haproxy_enable_ui: true
haproxy_ui_user: haproxy_user
haproxy_ui_password: haproxy
```

Example Playbook
----------------

```
    - hosts: servers
      roles:
         - { role: jebovic.haproxy }
```

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic
