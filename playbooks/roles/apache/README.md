Apache
======

Install and configure apache 2.4 with main macros and custom vhosts

Role Variables
--------------

```
# Default apache configuration
apache_user: www-data
apache_user_group: www-data
apache_port: 80
apache_www_root: /srv/www

# see macros name in templates/macros directory
apache_macros:
  - common-nofpm
  - common
  - commonREST
  - php-fpm
  - ssl-with-chain
  - ssl

# list modules you want to load in apache2.conf
apache_modules:
  - proxy.load
  - proxy_fcgi.load
  - proxy_http.load
  - proxy_ftp.load
  - proxy_connect.load
  - macro.load
  - rewrite.load
  - headers.load

# Add virtualhosts to sites-available and sites-enabled directories
apache_vhosts:
  - default
  - custom_vhosts

# Add your own vhosts, simply override apache_custom_vhosts to fit your needs
apache_custom_vhosts:
  - { ServerName: test.local, DocumentRoot: /srv/www }

# Specific link with php fpm
php_fpm_socket_path: /var/run/php5-fpm.sock
```

Example Playbook
----------------

```
    - hosts: servers
      roles:
         - { role: jebovic.apache }
```

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic
