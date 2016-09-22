Composer
========

Install composer for php applications

Requirements
------------

Works great with php-fpm

Role Variables
--------------

```
# Composer install configuration
composer_download_url: https://getcomposer.org/installer
composer_path: /usr/local/bin/composer
composer_version: ''
```

Example Playbook
----------------

```
    - hosts: servers
      roles:
         - { role: jebovic.composer }
```

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic
