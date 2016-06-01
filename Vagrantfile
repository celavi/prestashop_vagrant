# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Try to prevent 'stdin is not a tty'
  config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "bento/ubuntu-14.04"

  # Proxy Configuration Plugin for Vagrant
  if Vagrant.has_plugin?("vagrant-proxyconf")
    config.proxy.http     = "http://example.proxy.com:8080/"
    config.proxy.https    = "http://example.proxy.com:8080/"
    config.proxy.no_proxy = "localhost,127.0.0.1"
  end

  # Chef or Puppet would be classier, but sometimes a shell script does the trick:
  config.vm.provision :shell, path: "bootstrap.sh"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network "forwarded_port", guest: 80, host: 8081

  # Create a private network, which allows host-only access to the machine using a specific IP.
  config.vm.network :private_network, ip: "192.168.56.110"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"
  config.vm.synced_folder "./prestashop", "/var/www/html/prestashop",
    owner: "vagrant",
    group: "www-data",
    mount_options: ["dmode=775,fmode=664"],
    create: true
  config.vm.synced_folder "C:/Users/u106803/Projects/facebookpack", "/var/www/html/prestashop/modules/facebookpack",
    owner: "vagrant",
    group: "www-data",
    mount_options: ["dmode=775,fmode=664"],
    create: true
end
