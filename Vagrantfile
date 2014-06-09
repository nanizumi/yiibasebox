# -*- mode: ruby -*-
# vi: set ft=ruby :
# base box for running yii

Vagrant.configure("2") do |config|

    config.vm.provider :virtualbox do |v|
        v.name = "Yii-Vagrant"
        v.customize ["modifyvm", :id, "--memory", 512, "--cpus", 1]
    end

    config.vm.box = "trusty64"
    config.vm.box_url = "https://vagrantcloud.com/ubuntu/trusty64/version/1/provider/virtualbox.box"
	config.vm.host_name = "yiivagrant"

    config.vm.network :private_network, ip: "192.168.33.99"
    config.ssh.forward_agent = true

    # Port forwards
    config.vm.network "forwarded_port", guest: 80, host: 8888
    
	# PLUGINS
	# https://coderwall.com/p/7s40kg
	# vagrant plugin install vagrant-vbguest
	# vagrant plugin install vagrant-vbox-snapshot
	
	# set auto_update to false, if you do NOT want to check the correct 
	# additions version when booting this machine
	#config.vbguest.auto_update = false

	# do NOT download the iso file from a webserver
	#config.vbguest.no_remote = true


    # PROVISION
    # Ansible provisioning (you need to have ansible installed)
    #config.vm.provision "ansible" do |ansible|
    #    ansible.playbook = "ansible/playbook.yml"
    #end
    
	## Ansible will run in guest on windows machines
	config.vm.provision :shell, :path => "ansible/provision.sh"

    config.vm.synced_folder "./", "/vagrant", id: "vagrant-root" #, :nfs => true
end
