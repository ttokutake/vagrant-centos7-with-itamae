# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|
  config.vm.box = 'centos/7'

  # config.vm.network 'forwarded_port', guest: 80, host: 8080
  # config.vm.network 'private_network', ip: '192.168.33.10'

  # config.vm.synced_folder '../data', '/vagrant_data'

  # config.vm.provider :virtualbox do |vb|
  #   vb.memory = '1024'
  # end

  config.vm.provision :shell, inline: <<-SHELL
    yum install -y git
    yum install -y gcc make openssl-devel readline-devel

    su - vagrant -c '
      git clone https://github.com/asdf-vm/asdf.git $HOME/.asdf
      SET_ASDF_ENV="source $HOME/.asdf/asdf.sh && source $HOME/.asdf/completions/asdf.bash"
      eval $SET_ASDF_ENV
      echo $SET_ASDF_ENV >> ~/.bashrc

      asdf plugin-add ruby https://github.com/asdf-vm/asdf-ruby
      asdf install    ruby 2.4.1
      asdf global     ruby 2.4.1

      gem install itamae
    '
  SHELL
end
