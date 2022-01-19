# -*- mode: ruby -*-
# vi: set ft=ruby :

nodes = [
	{ :hostname => 'vm1', :ip => '192.168.0.200', :memory => 512, :cpu => 1, :boxname => "centos/7", :bridge => "eth1" },
        { :hostname => 'vm2', :ip => '192.168.0.201', :memory => 512, :cpu => 1, :boxname => "centos/7", :bridge => "eth1" }
    
]


Vagrant.configure("2") do |config|
  nodes.each do |node|
      config.vm.box_check_update = false
      config.vm.define node[:hostname] do |nodeconfig|
          nodeconfig.vm.box = node[:boxname]
          nodeconfig.vm.hostname = node[:hostname]
	  nodeconfig.vm.network :public_network, ip: node[:ip], bridge: node[:bridge]
          nodeconfig.vm.provider :virtualbox do |vb|
            vb.memory = node[:memory]
            vb.cpus = node[:cpu]
          end
        end
  end

#  config.vm.provision "ansible" do |ansible|
#     ansible.playbook = "playbook.yml"
#  end
  

end
