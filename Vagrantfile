# -*- mode: ruby -*-
# vi: set ft=ruby :

pool = ENV["POOL"] || "default"

Vagrant.configure(2) do |config|

  config.vm.synced_folder ".", "/vagrant", disabled: true


  config.vm.define "ansible1" do |ansible1|
    ansible1.vm.box = "generic/rhel8"
    ansible1.vm.hostname = "ansible1.local"
    ansible1.vm.provider :virtualbox do |v|
      v.memory = 2048
      v.cpus = 1
    end
  end

  config.vm.define "ansible2" do |ansible2|
    ansible2.vm.box = "generic/rhel8"
    ansible2.vm.hostname = "ansible2.local"
    ansible2.vm.provider :virtualbox do |v|
      v.memory = 2048
      v.cpus = 1
    end
  end
  
  if Vagrant.has_plugin?('vagrant-registration')
    config.registration.skip = true
    config.registration.unregister_on_halt = false
  end

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "site.yml"
    ansible.compatibility_mode = "2.0"
  end
end
