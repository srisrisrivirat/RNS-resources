# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'
HOST_IP = '192.168.56.65'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
config.vm.define "ubuntutest1" do |ubuntutest1|
ubuntutest1.vm.hostname = "ubuntutest1.rnstech.com"
ubuntutest1.vm.box = "ubuntu/trusty64"
ubuntutest1.vm.box_url = "ubuntu/trusty64"
ubuntutest1.vm.network :private_network,
      ip: HOST_IP,
      netmask: '255.255.255.0'
ubuntutest1.vm.network :forwarded_port, guest: 80, host: 8080
ubuntutest1.vm.synced_folder 'html', '/var/www/html'
ubuntutest1.vm.provision 'shell', path: 'provision.sh'	
end

config.vm.define "ubuntudev1" do |ubuntudev1|
ubuntudev1.vm.hostname = "ubuntudev1.rnstech.com"
ubuntudev1.vm.box = "ubuntu/trusty64"
ubuntudev1.vm.box_url = "ubuntu/trusty64"
ubuntudev1.vm.network :private_network,
      ip: '192.168.56.66',
      netmask: '255.255.255.0'
    ubuntudev1.vm.synced_folder 'html', '/var/www/html'
    ubuntudev1.vm.provision "shell", inline: <<-SHELL
    apt-get update
  apt-get install -y apache2
  SHELL
end
end