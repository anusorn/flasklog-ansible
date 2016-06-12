# -*- coding: utf-8; mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.hostname = ENV["VM_HOSTNAME"]
  config.vm.box = "digital_ocean"
  config.vm.box_url = "https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box"
  config.ssh.private_key_path = ["~/.ssh/digitalocean/id_rsa.digitalocean.com",
                                 "~/.ssh/bitbucket.org/id_rsa.bitbucket.org"]
  config.ssh.forward_agent = true

  config.vm.provider :digital_ocean do |provider, override|
    override.ssh.username = ENV["SSH_USERNAME"]
    provider.token = ENV["DIGITALOCEAN_API_KEY"]
    provider.image = "ubuntu-14-04-x64"
    provider.region = "sgp1"
    provider.size = "512mb"
    provider.setup = true
  end

  config.vm.provision :ansible do |ansible|
      ansible.playbook = "provision.yml"
      ansible.host_key_checking = false
      ansible.raw_ssh_args = [
          "-o ForwardAgent=yes"
      ]
      ansible.verbose = "VV"
  end

end
