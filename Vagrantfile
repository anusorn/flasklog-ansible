# -*- coding: utf-8; mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.hostname = ENV["VM_HOSTNAME"]
  config.ssh.forward_agent = true

  config.vm.provider :digital_ocean do |provider, override|
    override.vm.box = "digital_ocean"
    override.vm.box_url = "https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box"
    override.ssh.private_key_path = "~/.ssh/digitalocean/id_rsa.digitalocean.com"
    override.ssh.username = ENV["SSH_USERNAME"]
    provider.token = ENV["DIGITALOCEAN_API_KEY"]
    provider.image = "ubuntu-14-04-x64"
    provider.region = "sgp1"
    provider.size = "512mb"
    provider.setup = true
    provider.ssh_key_name = ENV["DIGITALOCEAN_SSH_KEY_NAME"]
  end

  # config.vm.provision :ansible do |ansible|
    # ansible.playbook = "provision.yml"
    # ansible.verbose = "VV"
  # end

end
