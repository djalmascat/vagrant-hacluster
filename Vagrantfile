# -*- mode: ruby -*-
# vi: set ft=ruby :

### PARAMETERS ###

VAGRANT_BOX = 'centos/7'
VM_NAME = 'dockernode'
VM_NETWORK = 'private_network' # set "private_network", ip: "192.168.33.10" or "public_network")
#VM_IP = "192.168.12.10" # set "dhcp" or the ip address "0.0.0.0" format
VM_MEMORY = '2048'

###
Vagrant.configure("2") do |config|
  (1..2).each do |i|
    config.vm.define "hacl#{i}" do |hacl|
      hacl.vm.provider "virtualbox" do |vm|
          vm.name = "hacl#{i}"
          vm.memory = 2048
        end
      hacl.vm.hostname = "hacln#{i}"
      hacl.vm.box = VAGRANT_BOX
      hacl.vm.network VM_NETWORK, ip: "192.168.12.1#{i}"
      hacl.vm.provision "shell", inline: <<-SHELL
        sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config 
        service sshd restart
        SHELL
    end
  end

end