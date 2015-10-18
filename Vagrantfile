# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.provision "shell", inline: <<-SCRIPT
    cp -rf /vagrant /home/vagrant
    chmod -x /home/vagrant/vagrant/local.ini

    apt-get update
    apt-get install -y python-pip

    pip install ansible

    export PYTHONUNBUFFERED=1
    ansible-playbook -i "/home/vagrant/vagrant/local.ini" "/home/vagrant/vagrant/site.yml"
  SCRIPT
end
