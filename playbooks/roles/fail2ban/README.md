Fail2ban
=========

Install and configure fail2ban, you can add your jails with yaml list variables

Role Variables
--------------

```
# fail2ban basic configuration
fail2ban_root_path: /etc/fail2ban
fail2ban_loglevel: 3
fail2ban_logtarget: /var/log/fail2ban.log
fail2ban_socket: /var/run/fail2ban/fail2ban.sock
fail2ban_pidfile: /var/run/fail2ban/fail2ban.pid

# fail2ban custom jails, do not forget to add DEFAULT jail from defaults/main.yml
fail2ban_jails:
  ssh:
    enabled:    true
    port:       ssh
    filter:     sshd
    logpath:    /var/log/auth.log
    maxretry:   6
```

Example Playbook
----------------

```
    - hosts: servers
      roles:
         - { role: jebovic.fail2ban }
```

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic
