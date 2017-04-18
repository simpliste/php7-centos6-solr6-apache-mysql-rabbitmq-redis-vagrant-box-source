# php7 Elasticsearch Nginx Mysql Centos Vagrant Box

Source environment for my [PHP7 CentOS Elasticsearch Mysql vagrant box](https://atlas.hashicorp.com/ajnijland/boxes/centos6-php7-elasticsearch-mysql). Provisioned using Ansible.

### Pre-reqs

* [Ansible](http://docs.ansible.com/ansible/index.html)

### Versions
> Basebox:centos/6 1703.01

* CentOS release 6.9 (Final)
* Nginx 1.12
* PHP 7.1.3
* MySQL 5.6.33
* Java JRE 8u112
* Kibana 4.6.3
    * Kibana sense plugin
* Ruby 2.1.4
* Beanstalkd 1.10
* Composer 1.2.2
* Elasticsearch 2.4.4
    * Elasticsearch Kopf plugin
    * Elasticsearch Mapper-attachement plugin
* Capistrano 2.15.9

### Instructions

* `vagrant up`
* Make any changes you need to the box. Be sure to reflect these changes in the provisioning scripts.
* Before packaging up the box, ssh in, and run the commands that are in the comments at the end of this readme.
* Package up the box with `vagrant package --output php7-centos-elasticsearch-mysql-0.1.0.box`. Replace `0.1.0` with the version number.
* Destroy the vm with `vagrant destroy --force`.
* Add the new box to vagrant's local list with: `vagrant box add php7-centos-elasticsearch-mysql-010 php7-centos-elasticsearch-mysql-0.1.0.box`. Again, replace `010` and `0.1.0` with the version number.
* Delete the `.vagrant` folder with `rm -rf .vagrant`.
* Test out the box by going to a different folder, running `vagrant init php7-centos-elasticsearch-mysql-010`, and changing the `Vagrantfile` to fit your needs. Next, run `vagrant up`, and ensure everything is working.
* Create a new version on Atlas.
* Add a new provider to the version. The type should be `virtualbox`. Upload the `.box` file output by the `vagrant package` command above.

### Pre-packaging commands

* `sudo rm /etc/udev/rules.d/70-persistent-net.rules`
* `sudo yum clean all`
* `sudo dd if=/dev/zero of=/bigemptyfile bs=1M`
* `sudo rm -rf /bigemptyfile`
* `sudo su`
* `history -c && exit`
* `cat /dev/null > ~/.bash_history && history -c && exit`
