# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'

ANSIBLE_PATH = "provision"

Vagrant.configure(2) do |config|
  # Disable default virtual box shared folder
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # Which centos box should be used? #https://atlas.hashicorp.com/centos/boxes/6/versions/
  config.vm.box = "centos/6"
  config.vm.box_version = "1708.01"

  config.vm.provider :virtualbox do |vb|
    vb.name = "pcsamrrvbs"
  end

  # Execute the ansible versions
  config.vm.provision :ansible do |ansible|
    ansible.playbook = File.join(ANSIBLE_PATH, "playbook.yml")
    ansible.verbose = true
  end
end

