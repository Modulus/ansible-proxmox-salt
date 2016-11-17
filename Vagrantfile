# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

      config.vm.hostname = "controller"
      config.vm.box = "ubuntu/trusty64"
      config.vm.network "private_network", ip: "192.168.77.200"

        # Only execute once the Ansible provisioner,
        # = when all the machines are up and ready.
        config.vm.provision "ansible_local" do |ansible|
          # Disable default limit to connect to all the machines
          ansible.limit = "controller"
          ansible.install = true
          ansible.playbook = "controller.yml"
          ansible.verbose  = true
          ansible.inventory_path = "inventory"
        end
  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
