# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
	config.vm.define "juice" do |juice|
		
  		juice.vm.box = "ubuntu/xenial64"

  		juice.vm.hostname = "juice"

  		juice.vm.network "private_network", ip: "192.168.33.10"

   	juice.vm.provider "virtualbox" do |v|
    # Hide the VirtualBox GUI when booting the machine
    	v.gui = false
		v.name = "juice-shop"
    # Customize the amount of memory on the VM:
    	v.memory = 2048
  	end

  	juice.vm.provision "file", source: "./default.conf", destination: "/tmp/juice-shop/default.conf"
   	juice.vm.provision :shell, path: "bootstrap.sh"
	end	


	config.vm.define "kali" do |kali|
  		kali.vm.box = "kalilinux/rolling"
  		kali.vm.hostname = "kali"
  # Create a forwarded port
		kali.vm.network "forwarded_port", guest: 80, host: 8080

		  # Create a private network. In VirtualBox, this is a Host-Only network
		kali.vm.network "private_network", ip: "192.168.33.20"

		  # VirtualBox specific settings
			kali.vm.provider "virtualbox" do |vb|
		    # Hide the VirtualBox GUI when booting the machine
				vb.gui = false
				vb.name = "kalilinux"
		    # Customize the amount of memory on the VM:
				vb.memory = 4096
			end
	
  # Provision the machine with a shell script
  # kali.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y crowbar
  # SHELL
  	end
end