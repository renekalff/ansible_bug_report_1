VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.insert_key = false

  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |v|
    v.linked_clone = true
    v.cpus = 1
    v.memory = 256
  end

  (1..2).each do |x|
    node_name = "host#{x}"
    config.vm.define node_name do |box|
      box.vm.hostname = node_name
    end
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "noop.yml"
  end
end
