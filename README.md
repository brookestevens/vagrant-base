# Starter Ubuntu box project template
Starter Ubuntu box for installing PHP 8, Node 14, NGINX, and MySQL

## Prereqs
Ansible and Vagrant must be installed on the host machine

## Setup
1. Modify Vagrantfile to sync the project directory
2. Set the vm.name
3. nginx conf files will probably have to be modified to work with the project
4. Run `vagrant up`
5. Run `vagrant provision` to run the playbook again

## Notes
1. php-fpm has to be started when the vm is restarted. Run `sudo systemctl start php-fpm`

2. Not sure if the mysql role will work on the first try because of the
default root password

3. The password of mysql is 'password'.
4. A new DB called drupal9 is also created in the mysql role
