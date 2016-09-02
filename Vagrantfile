# -*- mode: ruby -*-
# vi: set ft=ruby :
dfadfasdfas
# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = 'base'

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  config.nfs.functional = false

  config.vm.provider 'virtualbox' do |vb|
    vb.memory = '1024'
    vb.cpus = 1
  end

  config.vm.synced_folder 'puppet-filemapper', '/home/ubuntu/puppet-filemapper'
  config.vm.define 'ubu16' do |ubu|
    ubu.vm.box = 'ubuntu/xenial64'
    ubu.vm.provision 'shell', inline: 'apt-get update'
  end


  config.vm.define 'cent7_pup_network' do |cent7|
    cent7.vm.box = 'centos/7'

    cent7.vm.provision 'shell', inline: 'yum install -y epel-release'
    cent7.vm.provision 'shell', inline: 'sudo rpm -ivh https://yum.puppetlabs.com/puppetlabs-release-el-7.noarch.rpm'
    cent7.vm.provision 'shell', inline: 'yum install -y puppet ruby-devel vim'
  end
end
