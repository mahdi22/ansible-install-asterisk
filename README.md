<h1>ansible-install-asterisk</h1>
This is an ansible role to install Asterisk 13 tested on the GNU/Linux Centos 7.7 distribution, installed from cd image version minimal install.

# Requirements

- CentOS 7.x
- CentOS 8.x
- Ansible >= 2.7

# Installation

ansible-galaxy install mahdi22.ansible_install_asterisk

# Role Variables

file: vars/main.yml
* line 57
  - variable name: Driver
  - variable value: MSSQL # MSSQL if your cdr satabase server is MSSQL server
  - variable value: MYSQL # MYSQL if your cdr database server is Mysql Server or Mariadb Server
* line 58
  - variable name: SQL_HOST
  - variable value: localhost # Replace localhost with you database server name or IP address
* line 59
  - variable name: SQL_USER
  - variable value: dbuser # Replace dbuser with you sql user
* line 60
  - variable name: SQL_PASSWORD
  - variable value: dbpassword # Replace dbpassword with sql user password
* line 61
  - variable name: SQL_DATABASE
  - variable value: asterisk # Replace asterisk with the cdr database name
* line 62
  - variable name: SQL_TABLE
  - variable value: cdr # Replace cdr with your cdr table name

# Example Playbook
```sh
- hosts: servers
  roles:
    - role: mahdi22.install_asterisk
      become: yes
