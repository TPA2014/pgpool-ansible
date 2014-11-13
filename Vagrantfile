# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'ubuntu/trusty32'

  config.vm.define 'postgres1' do |machine|
    machine.vm.hostname = 'postgres1'
    machine.vm.network 'private_network', ip: '192.168.99.20'
  end

  config.vm.define 'postgres2' do |machine|
    machine.vm.hostname = 'postgres2'
    machine.vm.network 'private_network', ip: '192.168.99.21'
  end

  config.vm.define 'pgpool' do |machine|
    machine.vm.hostname = 'pgpool'
    machine.vm.network 'private_network', ip: '192.168.99.10'
    machine.vm.network 'forwarded_port', guest: 5432, host: 5432
  end

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  # config.ssh.forward_agent = true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Don't boot with headless mode
  #   vb.gui = true
  #
  #   # Use VBoxManage to customize the VM. For example to change memory:
  #   vb.customize ["modifyvm", :id, "--memory", "1024"]
  # end
  #
  # View the documentation for the provider you're using for more
  # information on available options.

  # Enable provisioning with Puppet stand alone.  Puppet manifests
  # are contained in a directory path relative to this Vagrantfile.
  # You will need to create the manifests directory and a manifest in
  # the file default.pp in the manifests_path directory.
  #
  # config.vm.provision "puppet" do |puppet|
  #   puppet.manifests_path = "manifests"
  #   puppet.manifest_file  = "default.pp"
  # end
end
