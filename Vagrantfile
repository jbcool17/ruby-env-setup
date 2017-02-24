# -*- mode: ruby -*-
# vi: set ft=ruby :

# https://manski.net/2016/09/vagrant-multi-machine-tutorial/
# Original bento box didn't work - Switched to trusty64
BOX_IMAGE = "ubuntu/trusty64"
NODE_COUNT = 2
MACHINES = ['development','production', 'staging']
Vagrant.configure("2") do |config|

  config.vm.define "development" do |subconfig|
    subconfig.vm.box = BOX_IMAGE
    subconfig.vm.hostname = "development"
    subconfig.vm.network :private_network, ip: "192.168.56.100"
    config.vm.synced_folder "./Projects", "/home/vagrant/Projects", type: "nfs"
  end

  (1..NODE_COUNT).each do |i|
    config.vm.define "#{MACHINES[i]}" do |subconfig|
      subconfig.vm.box = BOX_IMAGE
      subconfig.vm.hostname = "#{MACHINES[i]}"
      subconfig.vm.network :private_network, ip: "192.168.56.#{i + 100}"

      subconfig.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 2
      end
    end
  end

  # Install avahi on all machines & copy ssh key
  config.vm.provision "shell" do |s|
    ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
    s.inline = <<-SHELL
      apt-get install -y avahi-daemon libnss-mdns
      echo "<==== Copying KEYS ====>"
      echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
      echo #{ssh_pub_key} >> /root/.ssh/authorized_keys
      # known hosts
    SHELL
  end
end
