# Ansible LAMP Stack Playbook

This playbook deploys a LAMP (Linux, Apache, MySQL, and PHP) stack on an Ubuntu machine using Ansible.

## Requirements

* Ansible 2.4 or later installed on the control machine

* A target Ubuntu machine with SSH access

## Usage

1. Clone this repository to your local machine:

```
git clone https://github.com/koolwilly72/Ansible-Lamp-Stack.git
```

2. Edit the hosts file in the root of the repository to specify the IP address or hostname of the target Ubuntu machine.

```
web01 ansible_host=192.168.250.1 ansible_user=vagrant

[webserver]
web01
```

3. Edit the group_vars/all.yml file to specify the desired configuration for the LAMP stack:

```
---
# MYSQL root password
mysql_root_password: "changme123"

# Apache virtual host configuration
app_user: "www-data"
http_host: "example.com"
http_conf: "example.com.conf"
http_port: "80"
disable_default: true
```

4. Run the playbook:
```
ansible-playbook setup.yml
```

## What it does

The playbook performs the following tasks on the target host(s):

* Installs Apache, MySQL, and PHP packages
* Configures MySQL with a root password and a database and user for the application
* Creates an Apache virtual host with the specified server name, alias, and document root
* Deploys a PHP application to the document root using Git

## License

This playbook is licensed under the MIT license. See the LICENSE file for more details.
