# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box_url = "https://vagrantcloud.com/ubuntu/trusty64"
  config.vm.box = "ubuntu/trusty64"

  config.vm.hostname = "vagrant-touch-typing"
  config.vm.network :private_network, type: "dhcp"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end

  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.scope = :machine
  end

  config.vm.synced_folder ".", "/home/vagrant/touch-typing"

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end
end
