# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "hashicorp/precise32"

  # http://127.0.0.1:8081/smokeping/smokeping.cgi
  config.vm.network "forwarded_port", guest: 80, host: 8081
  config.vm.network "forwarded_port", guest: 443, host: 8443

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"

    # dummy hosts to exercise under Vagrant
    ansible.groups = {
      "myservergroup" => ["default"],
      "monitors" => ["default"]
    }
  end
end
