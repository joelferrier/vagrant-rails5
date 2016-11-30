# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos-7"
  config.vm.box_url = "https://s3-us-west-2.amazonaws.com/shrike/boxes/centos-7.box"
  config.vm.box_check_update = false

  config.vm.network "forwarded_port", guest: 3000, host: 3000

  config.vm.provider "virtualbox" do |vb|
    vb.cpus = "1"
    vb.memory = "1024"
  end

  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    sudo yum update -y
    sudo yum install -y libyaml-devel autoconf gcc-c++ patch readline-devel zlib-devel
    sudo yum install -y libffi-devel openssl-devel automake libtool bison sqlite-devel
    sudo yum install -y nodejs libxslt-devel libxml2-devel
    gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3
    curl -sSL https://get.rvm.io | bash -s stable --ruby
    echo "cd /vagrant" >> /home/vagrant/.bash_profile
  SHELL

end
