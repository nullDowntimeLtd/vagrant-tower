# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "puppetlabs/centos-6.6-64-nocm"

  config.vm.define "towerf", primary: true do |towerf|
    config.vm.provider :virtualbox do |vb, override|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
    end
    towerf.vm.network :private_network, ip: "192.168.250.20", virtualbox__intnet: true
  end

  config.vm.define "vmf1" do |vmf1|
    config.vm.provider :virtualbox do |vb, override|
      vb.customize ["modifyvm", :id, "--memory", "512"]
    end
    vmf1.vm.network :private_network, ip: "192.168.250.21", virtualbox__intnet: true
  end  

  config.vm.define "vmf2" do |vmf2|
    config.vm.provider :virtualbox do |vb, override|
      vb.customize ["modifyvm", :id, "--memory", "512"]
    end
    vmf2.vm.network :private_network, ip: "192.168.250.22", virtualbox__intnet: true
  end  

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "demo-site.yml"
    ansible.verbose = "v"
    ansible.sudo = true
    ansible.sudo_user = "root"
    ansible.host_key_checking = false
  end
end
