Mailhog
=======

Download, install and configure Mailhog, a great mail catcher

Role Variables
--------------

```
# Mailhog installation configuration
mailhog_install_dir: /usr/local/bin
mailhog_binary_url: https://github.com/mailhog/MailHog/releases/download/v0.2.0/MailHog_linux_amd64
mhsendmail_binary_url: https://github.com/mailhog/mhsendmail/releases/download/v0.2.0/mhsendmail_linux_amd64
sendmail_bin_path: /usr/bin/sendmail
mailhog_bin_path: "{{ mailhog_install_dir }}/mailhog"
mailhog_mhsendmail_path: "{{ mailhog_install_dir }}/mhsendmail"
```

Example Playbook
----------------

```
    - hosts: servers
      roles:
         - { role: jebovic.mailhog }
```

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic
