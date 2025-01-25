# -*- mode: ruby -*-
# vi: set ft=ruby :

#Параметры указываются в цикле
Vagrant.configure(2) do |config|
   config.vm.box = "generic/ubuntu2204"
#Можно указать конкретную версию сборки 
#Номера сборок можно посмотреть в Vagrant Cloud
#config.vm.box_version = "20220427.0.0"
   config.vm.provision "ansible" do |ansible|
#    ansible.verbose = "vvv"      # Уровень отображения процессов выполнения ansible
     ansible.compatibility_mode = "2.0"
     ansible.playbook = "playbook.yml"
     ansible.become = "true"
   end
 
   config.vm.provider "virtualbox" do |v|
   # Указываем количество ОЗУ и ядер процессора
     v.memory = 1024
     v.cpus = 1
   end
 
   config.vm.define "watchlog" do |watchlog|
     watchlog.vm.network "private_network", ip: "192.168.50.10", virtualbox__intnet: "net1"
     watchlog.vm.hostname = "wathclog"
     
   end
 
   config.vm.define "nginx" do |nginx|
     nginx.vm.network "private_network", ip: "192.168.50.11", virtualbox__intnet: "net1"
     nginx.vm.hostname = "nginx"
   end
 
   config.vm.define "fcgi" do |fcgi|
      fcgi.vm.network "private_network", ip: "192.168.50.12", virtualbox__intnet: "net1"
      fcgi.vm.hostname = "fcgi"
   end
end
