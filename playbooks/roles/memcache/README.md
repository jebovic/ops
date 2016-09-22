memcache
=========

Install and configure memcache

Role Variables
--------------

```
# Memcached basic configuration
memcache_log_file: /var/log/memcached.log
memcache_memory_size: 64
memcache_port: 11211
memcache_user: memcache
memcache_listen_address: 127.0.0.1
memcache_max_connections: 1024
```

Example Playbook
----------------

```
    - hosts: servers
      roles:
         - { role: jebovic.memcache }
```

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic
