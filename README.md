<h1>ansible-install-asterisk</h1>
This is an ansible role to install Asterisk on Redhat/CentOS 7 and 8 distribution, installed from cd image version minimal install.Specifically, the responsibilities of this role are to:

- Update server and reboot
- Install Asterisk dependency
- Install Dahdi package from source
- Install Asterisk Package from source
- Install libpri from source
- Configure Fail2ban
- Condigure Firewalld
- Configure Selinux
- Configure Asterisk CDR ODBC (optional)
- Configure Asterisk

# Requirements

- CentOS 7.x
- CentOS 8.x
- Ansible >= 2.7
- Asterisk 12
- Asterisk 13
- Asterisk 14

# Installation

ansible-galaxy install mahdi22.ansible_install_asterisk

# Role Variables
file: defaults/main.yml
Set configure_cdr_odbc: true to configure asterisk CDR ODBC. Only ODBC supported with this role:
  - Mysql/MariaDB
  - MSSQL
Set configure_cdr_odbc: false to not configure asterisk CDR ODBC.
Example:
```yaml
configure_cdr_odbc: true
```
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
    - role: mahdi22.asterisk
      become: yes
```
# Tests
This role was tested on Redhat end CentOS verion 7 and 8