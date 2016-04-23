# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

$script = <<SCRIPT
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install -y curl
sudo apt-get install -y mysql-client
sudo apt-get install -y nano
sudo apt-get install -y vim
sudo apt-get install -y php5-cli
sudo apt-get install -y php5-intl
sudo apt-get install -y php5-mcrypt
sudo apt-get install -y php5-gd
sudo apt-get install -y php5-curl
sudo apt-get install -y php5-mysql
curl -sS https://getcomposer.org/installer | php
sudo ln -s /home/vagrant/composer.phar /usr/local/bin/composer
curl -sSL https://get.docker.com/ > ~/install_docker
chmod +x ~/install_docker
sudo sh ~/install_docker
sudo usermod -aG docker vagrant

curl -L https://github.com/docker/compose/releases/download/1.4.0/docker-compose-`uname -s`-`uname -m` > ~/docker-compose
sudo mv ~/docker-compose /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  #POWER!
  config.vm.provider "virtualbox" do |v|
    v.memory = 2024
    v.cpus = 2
  end

  #BOX config
  config.vm.box = "ubuntu/trusty64"

  config.vm.network :private_network, ip: "VAGRANT_IP_ADDRESS"
  
  #SSH agent forwarding - required for git clone to work
  config.ssh.forward_agent = true

  config.vm.provision "shell", inline: $script
  
  # Synced folders
  config.vm.synced_folder ".", "/vagrant",
    id: "core",
    :nfs => true,
    :mount_options => ['nolock,vers=3,udp']
end

