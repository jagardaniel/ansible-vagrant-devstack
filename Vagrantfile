# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'

vars = YAML.load_file('vars.yml')

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "devstack"
  config.vm.network :private_network, ip: vars["devstack_network_host"]
  config.vm.provider :virtualbox do |vb|
    vb.memory = 4096
    vb.cpus = 2
    vb.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
  end
  config.ssh.forward_agent = true
  config.ssh.insert_key = false
  config.vm.provision "ansible", run: "always" do |ansible|
    ansible.playbook = "run.yml"
  end
end
