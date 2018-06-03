# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.omnibus.chef_version = :latest
  config.berkshelf.enabled = true
  config.berkshelf.berksfile_path = "./Berksfile"
  config.cache.auto_detect = true
  
  config.vm.provision :chef_solo do |chef|
    chef.log_level = "debug"
    chef.verbose_logging = true
    chef.add_recipe "apache2"
    chef.json = { :apache => { :default_site_enabled => true, :docroot_dir => '/vagrant/www' }} 
    end
end
