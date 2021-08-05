# -*- mode: ruby -*-
# vi: set ft=ruby :

script = <<-SHELL
sudo apt-get update
sudo apt-get -y upgrade

sudo apt-get install -y ansible python3-distutils git ubuntu-desktop qemu


export HOME=/home/vagrant

cd $HOME
if [ -e osbook ]; then
  cd osbook
  git pull
else 
  git clone https://github.com/uchan-nos/mikanos-build.git osbook
fi
cd $HOME/osbook/devenv
ansible-playbook -K -i ansible_inventory ansible_provision.yml

cd $HOME
if [ -e mikanos ]; then
  cd mikanos
  git pull
else 
  git clone https://github.com/lufeee/my-mikanos.git mikanos
fi

cd $HOME/edk2
if [ ! -e MikanLoaderPkg ]; then
  ln -s $HOME/mikanos/MikanLoaderPkg ./
fi
chown -R vagrant:vagrant $HOME/edk2 $HOME/mikanos $HOME/osbook

source $HOME/.profile
source $HOME/edk2/edksetup.sh
source $HOME/osbook/devenv/buildenv.sh

SHELL

Vagrant.configure("2") do |config|
  
  config.vm.box = "ubuntu/bionic64"
  
  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.cpus = "2"
    vb.memory = "4096"
    vb.customize [
      "modifyvm", :id,
      "--nested-hw-virt", "on"
    ]
  end
  
  config.vm.provision "shell", inline: script
  
end
