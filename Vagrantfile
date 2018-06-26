# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SCRIPT
echo I am provisioning...
date > /etc/vagrant_provisioned_at
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.host_name = "postgresql" 

  if Vagrant.has_plugin?("vagrant-proxyconf")
    config.proxy.http     = "http://proxy.msg.de:3128/"
    config.proxy.https    = "http://proxy.msg.de:3128/"
    config.proxy.no_proxy = "localhost,127.0.0.1"
  end

  config.vm.provision "shell", inline: $script
  config.vm.provision :shell, :path => "scripts/bootstrap.sh"
  
  # PostgreSQL Server port forwarding
  config.vm.network "forwarded_port", guest: 5432, host: 15432, host_ip: "127.0.0.1"
end
