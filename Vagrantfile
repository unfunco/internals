# vi: set ft=ruby

Vagrant.configure(2) do |config|
  config.vm.box = 'debian/jessie64'
  config.vm.network :private_network, ip: '10.20.30.40'

  config.vm.provision :shell, inline: <<-SH
sudo DEBIAN_FRONTEND=noninteractive apt-get -y update && apt-get -y upgrade && apt-get -y install \
autoconf \
automake \
bison \
build-essential \
libtool \
libxml2-dev \
ntp \
re2c \
valgrind
  SH

  config.vm.synced_folder '.', '/vagrant', disabled: true
  config.vm.synced_folder '../php-src', '/home/vagrant/php-src', type: :nfs
end
