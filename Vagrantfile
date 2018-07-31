# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.hostmanager.enabled = true
  config.hostmanager.ignore_private_ip = false

  config.vm.define 'docTool' do |cfg|
    cfg.vm.box_check_update = true
    cfg.vbguest.auto_update = true
    cfg.vm.synced_folder '.', '/vagrant', type: 'virtualbox'
    cfg.vm.synced_folder '/Users/jwilliams/Clouds/Box Sync/BNY Mellon/Documentation', '/Documentation', type: 'virtualbox'
    #cfg.vm.box = 'hashicorp/precise64'
    #cfg.vm.box = 'centos/7'
    cfg.vm.box = 'ubuntu/trusty64'
    #cfg.vm.box = 'abessifi/debian-jessie-ansible'
    #cfg.vm.box = 'abessifi/ubuntu-trusty-ansible'
    #cfg.vm.box  = 'abessifi/opensuse-13.2-ansible'
    cfg.vm.hostname = 'docTool'
    cfg.vm.network 'private_network', ip: '192.168.33.102'
    cfg.vm.provider 'virtualbox' do |vb|
      vb.name = 'docTool'
      vb.memory = 4096
      vb.cpus   = 2
    end
    cfg.vm.provision 'ansible' do |ansible|
      ansible.playbook = 'playbook.yml'
      ansible.limit = "all"
      ansible.verbose = ''
    end
  end

  ## Attempts to create a docker version of the doctoolchain
  #config.vm.define "dockerTool" do |dockerTool|
  #  dockerTool.vm.provider "docker" do |d|
  #    d.image = "erikadp/ubuntu-trusty-java8-oracle-tools"
  #  end
  #end
end
