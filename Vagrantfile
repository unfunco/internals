# vi: set ft=ruby

Vagrant.configure(2) do |config|
  config.vm.box = 'debian/jessie64'

  config.vm.provision :shell, inline: <<-SH
sudo DEBIAN_FRONTEND=noninteractive apt-get -y update
sudo DEBIAN_FRONTEND=noninteractive apt-get -y install \
autoconf \
automake \
bison \
build-essential \
git \
libtool \
libxml2-dev \
re2c \
valgrind
git clone https://github.com/php/php-src.git
sudo chown -R vagrant:vagrant php-src/
  SH
end
