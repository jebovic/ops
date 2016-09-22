Supervisor
==========

Install and configure supervisor, you can add your own programs with yaml variables

Role Variables
--------------

```
# Supervisor basic configuration
supervisor_socket: /tmp/supervisor.sock
supervisor_pidfile: /var/run/supervisord.pid
supervisor_log_path: /var/log/supervisord
supervisor_log_file: "{{ supervisor_log_path }}/supervisord.log"
supervisor_http_port: 9988
supervisor_http_username: supervisor_user
supervisor_http_password: supervisor

# Supervisor programs list, example with mailhog program
supervisor_programs:
  mailhog:
    command: /usr/local/bin/mailhog -api-bind-addr :8025 -ui-bind-addr :8025
    autostart: "true"
    autorestart: "true"
    stderr_logfile: "{{ supervisor_log_path }}/mailhog-stderr.log"
```

Example Playbook
----------------

```
    - hosts: servers
      roles:
         - { role: jebovic.supervisor }
```

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic
