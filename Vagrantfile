# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 4000, host: 4000

  config.vm.provision "shell", inline: <<-SHELL
#    sudo apt-get update
#    sudo apt-get -y install ruby ruby-dev make gcc nodejs
#    sudo gem install jekyll --no-rdoc --no-ri

    echo 'description "start jekyll serve"' | sudo tee -a /etc/init/jekyll.conf
    echo '' | sudo tee -a /etc/init/jekyll.conf
    echo 'start on vagrant-mounted' | sudo tee -a /etc/init/jekyll.conf
    echo '' | sudo tee -a /etc/init/jekyll.conf
    echo 'script' | sudo tee -a /etc/init/jekyll.conf
    echo '  cd /vagrant' | sudo tee -a /etc/init/jekyll.conf
    echo '  sudo -u vagrant /usr/local/bin/jekyll serve -H 0.0.0.0 --detach 2>&1 > /vagrant/jekyll.log' | sudo tee -a /etc/init/jekyll.conf
    echo 'end script' | sudo tee -a /etc/init/jekyll.conf

    sudo start jekyll
  SHELL
end
