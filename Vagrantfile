# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "almalinux/9"
  config.vm.provision "ansible" do |ansible|
    #ansible.verbose = "vvv"
    ansible.playbook = "provisioning/playbook.yml"
    ansible.become = "true"
  end

  config.vm.provider "virtualbox" do |v|
	  v.memory = 2048
    
  end

  config.vm.define "ns01" do |ns01|
    ns01.vbguest.installer_options = { allow_kernel_upgrade: true }
    ns01.vm.synced_folder ".", "/vagrant", disabled: true
    ns01.vm.network "private_network", ip: "192.168.50.10", virtualbox__intnet: "dns"
    ns01.vm.hostname = "ns01"
  end

  config.vm.define "client" do |client|
    client.vbguest.installer_options = { allow_kernel_upgrade: true }
    client.vm.synced_folder ".", "/vagrant", disabled: true
    client.vm.network "private_network", ip: "192.168.50.15", virtualbox__intnet: "dns"
    client.vm.hostname = "client"
  end

end
