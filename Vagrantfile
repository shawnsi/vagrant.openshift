VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "rhel-7.1-64"

    config.vm.provider "virtualbox" do |v|
      v.memory = 4096
      v.cpus = 2

      # Enable multiple guest CPUs if available
      v.customize ["modifyvm", :id, "--ioapic", "on"]
    end

    config.vm.define "master" do |master|
      master.vm.hostname = "ose3-master.example.com"

      master.vm.network :private_network, ip: "192.168.100.100"

      master.vm.network :forwarded_port, guest: 8443, host: 8443
      master.vm.network :forwarded_port, guest: 8444, host: 8444

      master.vm.synced_folder "certificates", "/var/lib/openshift/openshift.local.certificates"
    end


    config.vm.define "node1" do |node1|
      node1.vm.hostname = "ose3-node1.example.com"
      node1.vm.network :private_network, ip: "192.168.100.200"
    end

    config.vm.define "node2" do |node2|
      node2.vm.hostname = "ose3-node2.example.com"
      node2.vm.network :private_network, ip: "192.168.100.201"
    end

    config.vm.provision "ansible" do |ansible|
      ansible.groups = {
        "master" => ["master"],
        "node"   => ["master", "node1", "node2"],
      }

      ansible.playbook = "playbook.yml"
    end
end
