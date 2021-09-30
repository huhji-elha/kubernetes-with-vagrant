# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.define "controll-plane" do |config|
      config.vm.box = "ubuntu/bionic64"
        config.vm.provider "virtualbox" do |vb|
          vb.name = "controll-plane"
          vb.memory = "2048"
          vb.cpus = 2
        end
        config.vm.hostname = "controll-plane.example.com"
        config.vm.network "private_network", ip: "192.168.56.11"
    end
  
    config.vm.define "node1" do |config|
      config.vm.box = "ubuntu/bionic64"
        config.vm.provider "virtualbox" do |vb|
          vb.name = "node1"
          vb.memory = "1280"
          vb.cpus = 1
        end
        config.vm.hostname = "node1.example.com"
        config.vm.network "private_network", ip: "192.168.56.21"
        config.disksize.size = "5GB"
    end
  
    config.vm.define "node2" do |config|
      config.vm.box = "ubuntu/bionic64"
        config.vm.provider "virtualbox" do |vb|
          vb.name = "node2"
          vb.memory = "1280"
          vb.cpus = 1
        end
        config.vm.hostname = "node2.example.com"
        config.vm.network "private_network", ip: "192.168.56.22"
        config.disksize.size = "5GB"
    end
  
    config.hostmanager.enabled = true
    config.hostmanager.manage_guest = true  
  
    config.vm.provision "shell", inline: <<-SHELL
      sed -i 's/ChallengeResponseAuthentication no/ChallengeResponseAuthentication yes/g' /etc/ssh/sshd_config
      sed -i 's/archive.ubuntu.com/ftp.daum.net/g' /etc/apt/sources.list
      sed -i 's/security.ubuntu.com/ftp.daum.net/g' /etc/apt/sources.list
      systemctl restart ssh
    SHELL
  end
  