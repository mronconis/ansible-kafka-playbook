# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|
  #Define the number of nodes to spin up
  N = 2

  (1..N).each do |node_id|
    nid = (node_id - 1)

    config.vm.define "kafka-#{nid}.local.lan" do |node|
      node.vm.box = "centos/7"
      node.vm.hostname = "kafka-#{nid}.local.lan"
      node.vm.network :private_network, ip: "192.168.56.#{10 + nid}"

      node.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
        vb.cpus = 2 
      end

      node.vm.provision "ansible" do |ansible|
        ansible.playbook = "playbook.yaml"
        ansible.inventory_path = "inventories/vagrant"
        ansible.limit = "192.168.56.#{10 + nid}"
        ansible.extra_vars = {
          node_ip: "192.168.56.#{10 + nid}"
        }
      end

    end
  end
end