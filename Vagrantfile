# -*- mode: ruby -*-
# vi: set ft=ruby :


# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "ubuntu/trusty64"
  config.vm.network :private_network, ip: "10.3.45.3"
  
  config.vm.provision "ansible" do |ansible|
	    ansible.playbook = "ansible/playbook.yml"
	    ansible.host_key_checking = false
	    # uncomment to see more verbose ansible output
	    ansible.verbose = 'vvv'
  end
  
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--name", "Worpress Flux Inporter", "--memory", "2048", "--cpus", "4"]
    # To see boot-proccess uncomment next line
    # vb.gui = true
  end
  
  config.vm.synced_folder ".", "/vagrant", type: "nfs"

  config.vm.post_up_message = "Virtual Machine for '10.3.45.3' is ready
    Website:
        http://10.3.45.3/
    Important commands:
        vagrant ssh
            - Enter VM
        vagrant halt
            - Stop VM
        vagrant destroy
            - Remove VM
            (Your code is NOT affected, code is NOT stored on the VM)"

end
