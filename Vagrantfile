# -*- mode: ruby -*-
# vi: set ft=ruby :
# sudo usermod -aG docker vagrant

Vagrant.configure("2") do |config|

  1.times do |id|
    config.vm.define "k8s-#{id}" do |db|
      #db.vm.box = "bento/ubuntu-18.04"
      db.vm.box = "ubuntu/xenial64"
      db.vm.network "public_network", ip: "192.168.1.#{30+id}", bridge: "eth0"
      #db.vm.network "forwarded_port", guest: 9200, host: (9200+id)

      db.vm.provider "virtualbox" do |vb|
        vb.memory = "4096"
      end
      db.vm.provision "shell", inline: "cat /vagrant/id_rsa_virtualbox.pub >> .ssh/authorized_keys"
      db.vm.provision "shell", inline: "/vagrant/17.03.sh"
      db.vm.provision "shell", inline: "usermod -aG docker vagrant"
     end
  end

  3.times do |id|
    config.vm.define "k8s2-#{id}" do |db|
      #db.vm.box = "bento/ubuntu-18.04"
      db.vm.box = "ubuntu/xenial64"
      db.vm.network "private_network", ip: "172.28.128.#{13+id}"#, bridge: "eth0"
      #db.vm.network "forwarded_port", guest: 9200, host: (9200+id)

      db.vm.provider "virtualbox" do |vb|
        vb.memory = "4096"
      end
      db.vm.provision "shell", inline: "cat /vagrant/id_rsa_virtualbox.pub >> .ssh/authorized_keys"
      db.vm.provision "shell", inline: "/vagrant/17.03.sh"
      db.vm.provision "shell", inline: "usermod -aG docker vagrant"
     end
  end

end
