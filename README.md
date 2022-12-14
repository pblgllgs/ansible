# Ansible

__Primeros pasos en ansible__

## Add IPs in inventory file

### Paste in specific use group

```
[web_servers]
xxx.xxx.xxx.xxx

[db_servers]
xxx.xxx.xxx.xxx

[file_servers]
xxx.xxx.xxx.xxx
 
[workstations]
xxx.xxx.xxx.xxx
```

## Copy key in servers

### Generate key

```$bash
ssh-keygen -t ed25519 -C "DESCRIPTION"
```
### Copy key in all servers

```$bash
ssh-copy-id -i ~/path_of_private_key user@<ip>
```

## Install bootstrap

```$bash
ansible-playbook bootstrap.yaml --ask-become-pass
```

## Apply ansible-playbook in servers

```$bash
ansible-playbook site.yaml --ask-become-pass
```

## Add host_vars

If ubuntu distro, add file in host_vars/ with name __IP_ADDRESS.YAML__

```
apache_package_name: apache2
apache_service: apache2
php_package_name: libapache2-mod-php
ssh_users: "pblgllgs pablo"
ssh_template_file: sshd_config_ubuntu.j2
```

If centos distro, add file in host_vars/ with name __IP_ADDRESS.YAML__

```
apache_package_name: httpd
apache_service: httpd
php_package_name: php
ssh_users: "pblgllgs pablo"
ssh_template_file: sshd_config_centos.j2
```