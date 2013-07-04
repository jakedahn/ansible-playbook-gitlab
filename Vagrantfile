Vagrant.configure('2') do |config|

  # Ubuntu Quantal 12.10 from Brightbox
  config.vm.box = "quantal64"
  config.vm.box_url = 'http://images.notprod.pl/vagrant/quantal64.box'

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", 2048, "--cpus", 1]
  end

  config.vm.network :forwarded_port, guest: 5000, host: 5000
  config.vm.network :forwarded_port, guest: 5001, host: 5001
  config.vm.network :forwarded_port, guest: 80, host: 8081

  # Ansible Support
  config.vm.provision :ansible do |ansible|
    ansible.inventory_file = "vagrant-inventory.ini"
    ansible.playbook = "gitlab.yml"
  end

end
