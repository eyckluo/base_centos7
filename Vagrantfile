# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SHELL
  yum install -y ansible
  yum install -y vim tmux mlocate tree ack
  yum install -y yum-utils device-mapper-persistent-data lvm2
  yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
  yum makecache fast
  yum install -y docker-ce
  systemctl start docker
SHELL

Vagrant.configure("2") do |config|
  config.vm.box_check_update = false
  config.vm.box = "centos/7"
  config.vm.synced_folder ".", "/vagrant", type: "virtualbox"
  config.vm.provision "shell", inline: $script
  config.vm.network "forwarded_port", guest: 8080, host: 8080
end
