# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doina
Vagrant.configure("2") do |config|
  config.vm.define :master do |master_config|
      if Vagrant.has_plugin?("vagrant-cachier")
      config.cache.scope = :box
      end
      master_config.vm.box =  "bento/centos-7"
      master_config.vm.hostname = "tank01"           
      master_config.vm.network "forwarded_port", guest:80, host:8282
      master_config.vm.network :private_network, ip: "192.168.33.10"
      master_config.vm.synced_folder "vagrant", "/vagrant"
      master_config.omnibus.chef_version = "11.4.0"
      master_config.vm.provider :virtualbox do |vb|
	  file_to_disk = 'C:/Users/Anton_Kolupayev/vagrant/vagrant_hdd.vdi'
	  unless File.exist?(file_to_disk)
	   vb.customize ['createhd', '--filename', file_to_disk, '--size', 500 * 1024]
	  end
          vb.customize ["modifyvm", :id, "--memory", "2048"]
          vb.customize ["modifyvm", :id, "--cpus", "2"]
	  vb.customize ['storageattach', :id, '--storagectl', 'SATA Controller', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', file_to_disk]
      end                                                         
#      master_config.vm.provision "chef_solo" do |chef|
#          chef.add_recipe "sap-keyc"
#      end
  end

end
