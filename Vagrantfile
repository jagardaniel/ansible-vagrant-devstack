# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  config.vm.hostname = "devstack"
  config.vm.network :private_network, ip: "192.168.27.100"
  #config.vm.network :private_network, ip: "192.168.0.100", :auto_config => false
  config.vm.network :private_network, ip: "192.168.40.100"
  config.vm.provider :virtualbox do |vb|
    vb.memory = 4096
    vb.cpus = 2
    vb.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
  end
  config.ssh.forward_agent = true
  config.ssh.insert_key = false
  config.vm.provision "ansible", run: "always" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "run.yml"
  end
end
