# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Используем стандартный легкий образ Ubuntu, который всегда доступен
  config.vm.box = "ubuntu/jammy64"

  config.vm.define "PHP Backend" do |node|
    node.vm.hostname = "PHP Backend"
    node.vm.network "private_network", ip: "192.168.10.42"

    # Проброс портов (например, веб-сервер и SSH)
    node.vm.network "forwarded_port", guest: 80, host: 8080
    node.vm.network "forwarded_port", guest: 443, host: 4430
    node.vm.network "forwarded_port", guest: 22, host: 2242

    # Синхронизация текущей папки проекта в веб-корень виртуальной машины
    node.vm.synced_folder ".", "/vagrant", type: "rsync"
  end
end