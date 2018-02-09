
# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
 # config.vm.box = "geerlingguy/ubuntu1604"
 # config.vm.box = "geerlingguy/centos7"
  config.vm.box = "centos/7"
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.name = "hardening"
    v.memory = 512
    v.cpus = 2
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  config.vm.hostname = "hardening"
  config.vm.network :private_network, ip: "192.168.33.34"

  # Set the name of the VM. See: http://stackoverflow.com/a/17864388/100134
  config.vm.define :hardening do |hardening|
  end

  # Ansible provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "./playbook.yml"
    ansible.inventory_path = "./inventory"
    ansible.sudo = true
  end

end