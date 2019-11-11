# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "bento/ubuntu-18.04"

  config.vm.network "forwarded_port", guest: 27017, host: 27017
  config.vm.network "private_network", ip: "192.168.33.11"

  config.vm.provision "shell", inline: <<-SCRIPT
    export DEBIAN_FRONTEND=noninteractive

    cp -rf /vagrant /home/vagrant
    chmod -x /home/vagrant/vagrant/local.ini

    apt-get update
    apt-get install -y python-dev
    apt-get install -y python-pip
    apt-get install -y libffi-dev

    pip install pyopenssl
    pip install markupsafe
    pip install ansible

    export PYTHONUNBUFFERED=1
    ansible-playbook -i "/home/vagrant/vagrant/local.ini" "/vagrant/playbooks/lab-mongodb.yml"
  SCRIPT
end
