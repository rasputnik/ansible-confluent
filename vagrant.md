# requirements

* Virtualbox 5
* vagrant
* Ansible 1.9.x
* the vagrant hostmanager plugin (to edit /etc/hosts and fix name resolution)

# install

    vagrant plugin install vagrant-hostmanager
    vagrant up
    ansible-playbook -i vagrant/ site.yml
    # (playbooks are idempotent, safe to run them multiple times to reset configs etc)

This will get you 3 brokers you can access from your desktop.

## common settings

_(NB: these are subject to change, the Ansible playbooks are authoratative)_

your broker list will be "broker1:9092,broker2:9092,broker3:9092"

your zookeeper list is "broker1:2181,broker2:2181,broker3:2181"

## gotchas

* topic deletion is off by default
* no tunings have been made to stock configs
