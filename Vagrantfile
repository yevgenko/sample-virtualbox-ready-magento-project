# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.hostname = "magento-example-berkshelf"
  config.vm.box = "Ubuntu precise 64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.network :private_network, ip: "33.33.33.10"
  config.vm.boot_timeout = 120
  config.berkshelf.enabled = true

  config.vm.synced_folder ".", "/var/www/magento",
    mount_options: ['dmode=775', 'fmode=664']

  config.vm.provision :chef_solo do |chef|
    chef.json = {
      :mysql => {
        :bind_address => '127.0.0.1',
        :server_root_password => 'rootpass',
        :server_debian_password => 'debpass',
        :server_repl_password => 'replpass'
      },
      :magento => {
        :url => '', # we already have magento in a working tree
        :db => {
          :password => 'magepass'
        }
      },
      :nginx => {
        :group => 'vagrant' # since directory will be mounted with this group
      },
      "php-fpm" => {
        :pool => {
          :magento => {
            :group => 'vagrant' # since directory will be mounted with this group
          }
        }
      }
    }

    chef.run_list = [
      "recipe[magento::default]"
    ]
  end
end
