Vagrant.configure("2") do |config|

  config.vm.box = "bento/ubuntu-18.04"
  config.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 2
  end

  config.vm.define "node-2" do |machine|
    machine.vm.network "private_network", ip: "192.168.50.12"
    machine.vm.hostname = "node-2"
    machine.vm.provision "shell" , inline: $script
  end

  config.vm.define "node-1" do |machine|
    machine.vm.network "private_network", ip: "192.168.50.11"
    machine.vm.hostname = "node-1"
    machine.vm.provision "shell" , inline: $script
  end

  config.vm.define 'master' do |machine|
    machine.vm.network "private_network", ip: "192.168.50.10"
    machine.vm.hostname = "master"
    machine.vm.synced_folder "./", "/vagrant", owner: "vagrant", mount_options: ["dmode=775,fmode=600"]
    machine.vm.provision "shell" , inline: $script

    machine.vm.provision :ansible_local do |ansible|
      ansible.playbook       = "master-playbook.yml"
      #ansible.playbook       = "master-test.yml"
      ansible.verbose        = true
      ansible.install        = true
      ansible.limit          = "all"
      ansible.inventory_path = "inventory"
      ansible.config_file = "ansible.cfg"
    end
    
  end

$script = <<SCRIPT
echo "Running script..."
sudo cp /vagrant/hosts /etc/hosts
sudo apt-get update -y

SCRIPT


end