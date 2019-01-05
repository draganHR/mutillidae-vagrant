# -*- mode: ruby -*-
# vi: set ft=ruby ts=2 sw=2 expandtab:

VAGRANTFILE_API_VERSION = "2"

ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "centos/7"
  config.vm.host_name = "mutillidae-vm"
  config.vm.define "mutillidae" do |vm|  # set vm name
  end

  config.vm.network "private_network", type: "dhcp"
  config.vm.synced_folder "", "/vagrant", type: "virtualbox", id: "vagrant-root"
  config.vm.provision :shell, :path => "bootstrap", :env => {"VOID" => "#{ENV['VOID']}"}
  config.vbguest.auto_reboot = true

  config.vm.provider :virtualbox do |vb|
    # set default memory and cpus on first boot
    if not File.exists?(".vagrant/machines/mutillidae/virtualbox/action_provision")
      vb.memory = 1024
      vb.cpus = 2
    end
  end

end
