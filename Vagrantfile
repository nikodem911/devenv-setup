Vagrant.configure("2") do |config|
  config.vm.box = "devtools-deb9"

  config.vm.provider :virtualbox do |vb|
    vb.gui = true
	  vb.memory = 4096
	  vb.cpus = 2
	  vb.customize ["modifyvm", :id, "--uartmode1", "disconnected"]
	  vb.customize ["modifyvm", :id, "--vram", "256"]
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.groups = {
      'sde' => ['default']
    }
	  ansible.become = true
	  ansible.galaxy_role_file = 'provisioning/requirements.yml'
    ansible.playbook = "provisioning/playbook.yml"
    ansible.version = "2.5.4"
  end  
end