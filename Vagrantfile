# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "archlinux/archlinux"
  (1..3).each do |i|
    config.vm.define vm_name = "server-#{i}" do |config|
      config.vm.hostname = vm_name
      ip = "172.21.12.#{i+10}"
      config.vm.network :private_network, ip: ip
      #config.vm.provision :shell, :inline => "DEBIAN_FRONTEND=noninteractive apt-get update && apt-get install -yq tmux", :privileged => true
      config.vm.provider :libvirt do |libvirt|
        libvirt.storage :file, :size => '20G'
        libvirt.cpu_mode = 'host-passthrough'
      end
    end
  end
  config.vm.define vm_name = "client" do |config|
    config.vm.hostname = vm_name
    ip = "172.21.12.10"
    config.vm.network :private_network, ip: ip
    #config.vm.provision :shell, :inline => "DEBIAN_FRONTEND=noninteractive apt-get update && apt-get install -yq tmux", :privileged => true
  end
end
