# -*- mode: ruby -*-
# vim: set ft=ruby :

Vagrant.configure('2') do |config|
  config.vm.box = "centos/7"

  config.vm.define :control do |control|
    control.vm.hostname = "controller"
    control.vm.network :public_network
    control.vm.network :private_network, ip: "192.168.11.101"
    control.vm.provider :kvm do |kvm, override|
      kvm.memory_size = '1024m'
   end
    control.vm.provider :libvirt do |libvirt, override|
      libvirt.memory = 1024
      libvirt.nested = true
      libvirt.cpus = 2
    end
  end

  config.vm.provision "shell", inline: <<-SHELL
    mkdir -p ~root/.ssh
    cp ~vagrant/.ssh/auth* ~root/.ssh
    yum install -y mdadm smartmontools hdparm gdisk
  SHELL
end
