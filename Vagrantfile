NUM_MASTER_NODE = 1
NUM_WORKER_NODE = 2

IP_NW = "<ip-pool>"
MASTER_IP_START = 1
NODE_IP_START = 2
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  # Disable automatic box update checking.
  config.vm.box_check_update = false

  # Provision Master Nodes
  (1..NUM_MASTER_NODE).each do |i|
      config.vm.define "master0#{i}" do |node|
        node.vm.provider "virtualbox" do |vb|
            vb.name = "master0#{i}"
            vb.memory = 2048
            vb.cpus = 2
        end
        node.vm.hostname = "master0#{i}"
        node.vm.network :private_network, ip: IP_NW + "#{MASTER_IP_START + i}"
        node.vm.network "forwarded_port", guest: 22, host: "#{2710 + i}"
        end
      end
  end

  # Provision Worker Nodes
  (1..NUM_WORKER_NODE).each do |i|
    config.vm.define "worker0#{i}" do |node|
        node.vm.provider "virtualbox" do |vb|
            vb.name = "worker0#{i}"
            vb.memory = 1024
            vb.cpus = 2
        end
        node.vm.hostname = "worker0#{i}"
        node.vm.network :private_network, ip: IP_NW + "#{NODE_IP_START + i}"
        node.vm.network "forwarded_port", guest: 22, host: "#{2720 + i}"
        end
    end
  end
end
