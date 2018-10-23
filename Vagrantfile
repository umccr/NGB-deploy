# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/cosmic64"

  config.vm.provider "virtualbox" do |vb|
    vb.cpus = "4"
    vb.memory = "4096"
  end
 
  config.vm.hostname = "localhost"

  # Pre-seed ubuntu with Ansible installation
  #config.vm.provision "shell",
  #  inline: "sudo apt update && sudo apt install -y python3-venv && /usr/bin/python3 -mvenv ansible && source ./ansible/bin/activate && pip3 install ansible"

  # Deploy the ansible role(s)/playbook(s) 
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    #ansible.verbose = 'vvvv'
    ansible.extra_vars = { ansible_ssh_user: 'vagrant', ansible_python_interpreter: '/usr/bin/python3' }
	  ansible.compatibility_mode = "2.0"
  end
end
