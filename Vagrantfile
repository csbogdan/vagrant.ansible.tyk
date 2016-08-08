# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true


   # Ansible configuration
   config.vm.provision "ansible" do |ansible|
     ansible.playbook = "deploytyk.yml" 
     # ansible.raw_arguments  = ""
     # ansible.extra_vars = {}
     # ansible.verbose=""
     ansible.groups = {
        "tyk" => [ "tyk" ]
     }
   end  


  config.vm.define "tyk" , autostart: true, primary: true do |tyk|
    tyk.vm.box = "hashicorp/precise64"
    tyk.ssh.insert_key = false
    tyk.vm.hostname = "tyk"
    tyk.vm.network :private_network, ip: "192.168.50.101"
    tyk.vm.network :forwarded_port, guest: 3000, host: 3000
    tyk.vm.network :forwarded_port, guest: 8080, host: 8080
    tyk.hostmanager.aliases = [ "my-tyk-instance.com", "portal-instance.com" ]

    #VirtualBox settings
    tyk.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1024"]
      vb.customize ["modifyvm", :id, "--name", "tyk"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.customize ["modifyvm", :id, "--ioapic", "on"]
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "75"]
      vb.customize ["modifyvm", :id, "--paravirtprovider", "kvm"]
    end   
    tyk.vbguest.auto_update = true
  end

end
