Ansible Role: Traefik WordPress
=========

This Ansible playbook will Deploy & run Docker Compose project for WordPress instance. It will also configure Let's Encrypt certificates for specified domain. It consists of 3 separate containers running:
* WordPress (PHP7 FPM)
* Nginx 
* Traefik (enabled with Let's Encrpt HTTPS encryption)
* MariaDB

This role was created as part of [Traefik Wordpress](https://github.com/doko89/traefik-wordpress)

Requirements
------------

For this role to work, it is required to have have Docker and Docker Compose installed and setup. If you haven't done this already (manually)

Role Variables
--------------

## acme
email: user@gmail.com
```
### example vars.yml
--------------------

```
---
# defaults file for wordpress-docker
system_user: ubuntu
project: domain
stage: local #local or production
domain: domain.com      
compose_project_dir: /home/{{ system_user }}/{{ domain }}

## wordpress
wp_version: 4.9.6
php_fmp_version: fpm-alpine
wp_db_name: wordpress
wp_db_tb_pre: wp_
wp_db_host: mysql
wp_db_psw: mysqlpassword

## acme
email: user@mail.com
```


Example Playbook
----------------

```
- hosts: all
  vars_files:
  - ./vars.yml
  roles:
  - traefik-wordpress

```

License
-------

GPLv3
