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
    end

    config.vm.define "node1" do |node1|
      node1.vm.hostname = "node1.openshift"
    end

    config.vm.define "node2" do |node2|
      node2.vm.hostname = "node2.openshift"
    end

    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
end
