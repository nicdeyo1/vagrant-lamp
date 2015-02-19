# -*- mode: ruby -*-
# vi: set ft=ruby :
 
# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"
 
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.host_name = "localhost"
  config.vm.provider "virtualbox" do |v|
    v.name = "Vagrant LAMP"
  end
  config.vm.network :forwarded_port, host: 8080, guest: 80
  config.vm.network :forwarded_port, host: 33066, guest: 3306
  config.vm.network :forwarded_port, host: 2200, guest: 22

  config.vm.provider "virtualbox" do |v|
  	v.memory = 1024
  	v.cpus = 2
  	v.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
  end
  config.vm.provision :shell, path: "setup.sh"

  #!!!
  #			SET WEB ROOT HERE
  #!!!
  config.vm.synced_folder "public", "/var/www/public"

end