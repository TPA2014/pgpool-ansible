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

    machine.provision 'ansible' do |ansible|
      ansible.playbook = 'provisioning/playbook.yml'
      ansible.limit    = 'all'
      ansible.sudo     = true
      ansible.groups   = {
        'postgres' => ['postgres1', 'postgres2'],
        'pgpool'   => ['pgpool'],
      }
  end
end
