# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

Vagrant.configure(2) do |config|

  config.vm.box = "hashicorp/precise64"

  config.vm.provision "file", source: "~/projects/vagrant/files/git-config", destination: "~/.gitconfig"
  
  config.vm.provision "shell" , path: "https://raw.githubusercontent.com/rezakay/vagrant/master/scripts/ubuntu-common.sh"
  


  #config.vbguest.auto_update = false;

  config.vm.define "web" do |web|

   web.vm.hostname = "web-server"

   web.vm.network "forwarded_port", guest: 80, host: 8080

   #private network for web and db servers communication
   web.vm.network "private_network", ip: "192.168.10.2"

   web.vm.provision "shell" , path: "https://raw.githubusercontent.com/rezakay/vagrant/master/scripts/ubuntu-web.sh"

  end
  
  config.vm.define "db" do |db|
   db.vm.hostname = "database-server"

   #private network for web and db servers communication
   db.vm.network "private_network", ip: "192.168.10.3"

   db.vm.provision "shell" , path: "https://raw.githubusercontent.com/rezakay/vagrant/master/scripts/ubuntu-db.sh"
  
  end

  
end
