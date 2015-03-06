VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "rhel-7.0-64"

    config.vm.provider "virtualbox" do |v|
      v.memory = 4096
      v.cpus = 2

      # Enable multiple guest CPUs if available
      v.customize ["modifyvm", :id, "--ioapic", "on"]
    end

    config.vm.define "broker" do |broker|
      broker.vm.hostname = "broker.openshift"

      broker.vm.network :private_network, ip: "192.168.100.100"

      broker.vm.network :forwarded_port, guest: 8443, host: 8443
      broker.vm.network :forwarded_port, guest: 8444, host: 8444
    end

    config.vm.define "node1" do |node1|
      node1.vm.hostname = "node1.openshift"
      node1.vm.network :private_network, ip: "192.168.100.200"
    end

    config.vm.define "node2" do |node2|
      node2.vm.hostname = "node2.openshift"
      node2.vm.network :private_network, ip: "192.168.100.201"
    end

    config.vm.provision "ansible" do |ansible|
      ansible.groups = {
        "broker" => ["broker"],
        "node"   => ["broker"],
      }

      ansible.playbook = "playbook.yml"
    end
end
