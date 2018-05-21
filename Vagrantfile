# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box_check_update = true
  #config.vbguest.iso_path = "#{ENV['HOME']}/Downloads/VBoxGuestAdditions.iso"
  #config.vbguest.iso_path = "/Applications/VirtualBox.app/Contents/MacOS/VBoxGuestAdditions.iso"
  config.vbguest.auto_update = true
  config.vm.synced_folder '.', '/vagrant', type: 'virtualbox'
  config.vm.synced_folder '/Users/jwilliams/Clouds/Box Sync/BNY Mellon/Documentation', '/Documentation', type: 'virtualbox'

  config.hostmanager.enabled = true
  config.hostmanager.ignore_private_ip = false

  config.vm.define 'docTool' do |cfg|
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
      vb.memory = 2024
      vb.cpus   = 2
    end
    cfg.vm.provision 'ansible' do |ansible|
      ansible.playbook = 'playbook.yml'
      ansible.limit = "all"
      ansible.verbose = ''
    end
  end

end
