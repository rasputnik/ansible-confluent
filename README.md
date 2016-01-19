Confluent.io cluster on centos 6.

Cluster of CentOS 6.x nodes. Each runs:

* a zookeeper
* a kafka node
* a schema registry instance

all configs are stock from the Confluent distro,
barring changes to setup HA zookeeper and configure
each component to talk to that.

See **vagrant.md** for Vagrant instructions.

# install

    vagrant plugin install vagrant-hostmanager
    vagrant up
    ansible-playbook -i vagrant/ site.yml

Then see **USAGE.md**.
