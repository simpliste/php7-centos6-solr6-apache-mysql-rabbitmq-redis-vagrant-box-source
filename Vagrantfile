# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'

ANSIBLE_PATH = "provision"

Vagrant.configure(2) do |config|
  # Enable virtual box shared folder for usage on windows (default is rsync)
  config.vm.synced_folder ".", "/vagrant", type: "virtualbox"

  # Which centos box should be used? #https://atlas.hashicorp.com/centos/boxes/6/versions/1610.01
  config.vm.box = "centos/6"
  config.vm.box_version = "1610.01"

  # Execute the ansible versions
  config.vm.provision :ansible do |ansible|
    ansible.playbook = File.join(ANSIBLE_PATH, "playbook.yml")
    ansible.verbose = true
  end
end

