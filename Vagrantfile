# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "dummy"
  config.ssh.pty = true
  config.omnibus.chef_version = :latest

  config.vm.provision "chef_solo" do |chef|
    chef.add_recipe "telnet"
  end

  config.vm.provider :aws do |aws, override|
    aws.access_key_id = ENV['AWS_ACCESS_KEY_ID']
    aws.secret_access_key = ENV['AWS_SECRET_ACCESS_KEY']
    aws.keypair_name = "vagrant"
    aws.instance_type = "t2.micro"
    aws.ami = "ami-b66ed3de"
    aws.security_groups = "default"
    override.ssh.username = "ec2-user"
    override.ssh.private_key_path = ENV['AWS_SSH_KEY'] 
  end
end
