# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SCRIPT
echo I am provisioning...
date > /etc/vagrant_provisioned_at
SCRIPT

$http_proxy = ""
$https_proxy = ""

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.host_name = "postgresql" 

  if Vagrant.has_plugin?("vagrant-proxyconf")
    config.proxy.http     = $http_proxy
    config.proxy.https    = $https_proxy
    config.proxy.no_proxy = "localhost,127.0.0.1"
  end

  config.vm.provision "shell", inline: $script
  config.vm.provision :shell, :path => "scripts/postgresql.sh"
  
  # PostgreSQL Server port forwarding
  config.vm.network "forwarded_port", guest: 5432, host: 15432, host_ip: "127.0.0.1"
end
