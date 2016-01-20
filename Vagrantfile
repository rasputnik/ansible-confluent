# -*- mode: ruby -*-
# vi: set ft=ruby :

## if you change these, change vagrant/hosts too
#
# would love to have this read vagrant/hosts directly.

hosts = [
  {:name => "broker1", :ip => "10.20.10.10", :ram => 1900},
  {:name => "broker2", :ip => "10.20.10.20", :ram => 1900},
  {:name => "broker3", :ip => "10.20.10.30", :ram => 1900},
]

Vagrant.configure("2") do |config|

  # setup /etc/hosts on each vm
  # - requires the vagrant-hostmanager plugin
  config.hostmanager.enabled = true
  # set to 'false' if you don't wan't to manage _your_ /etc/hosts
  config.hostmanager.manage_host = true
  config.hostmanager.include_offline = true

  hosts.each do |host|
    config.vm.define host[:name] do |c|

      c.vm.box = "box-cutter/centos66"
      c.vm.box_version = "2.0.11"

      # stop Vagrant 'helping'
      c.ssh.insert_key = false

      c.vm.hostname = host[:name]

      c.vm.network :private_network, ip: host[:ip], netmask: "255.255.255.0"

      c.vm.provider("virtualbox") do |vb|
        vb.memory = host[:ram]
      end

      # turn off shared folder
      c.vm.synced_folder ".", "/vagrant", :disabled => true
    end
  end
end
