# -*- mode: ruby -*-
# vi: set ft=ruby :

# Make sure vagrant cloud is also used with older vagrant versions.
Vagrant::DEFAULT_SERVER_URL.replace('https://vagrantcloud.com')

Vagrant.configure("2") do |config|

 config.vm.define "vagrant"

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "nrclark/xenial64-minimal-libvirt"

  # Sync vagrant folder with rsync
  config.vm.synced_folder './', '/vagrant', type: 'rsync'

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "10.10.10.2"

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "provision.yaml"
    ansible.inventory_path = "inventory/vagrant"
  end
end
