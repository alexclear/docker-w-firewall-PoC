# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.define "localhost" do |localhost|
    localhost.vm.box='ubuntu/xenial64'
    localhost.vm.provider :virtualbox do |v|
      v.name = "localhost"
    end
  end

  config.vm.provision "shell",
    inline: "apt-get install -y python"
  
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "site.yml"
    ansible.sudo = true
    ansible.extra_vars = {
      lxd_zfs_pool_name: 'zpool',
    }
  end
end
