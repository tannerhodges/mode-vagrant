# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

    # Box settings
    config.vm.box = "mode-tanner-3.0.0"
    config.vm.box_url = "mode-tanner-3.0.0.box"
    config.vm.provider "virtualbox" do |vm|
        vm.name = "MODE Tanner 3.0.0 (CentOS 6.x)"
        vm.memory = "480"
    end

    # IP address to use for local hosts
    config.vm.network "private_network", ip: "33.33.33.33"
    # Share the site at `vhosts/default/` to all devices on your Wifi network
    config.vm.network "public_network", :bridge => "en1: Wi-Fi (AirPort)"
    # ... or Ethernet
    # config.vm.network "public_network", :bridge => "en0: Ethernet 1"

    # Forward ports for emote debugging
    config.vm.network :forwarded_port, guest: 80,   host: 8080   # Apache
    config.vm.network :forwarded_port, guest: 3306, host: 3306   # MySQL
    config.vm.network :forwarded_port, guest: 8888, host: 8888   # Remote Debug

    # Setup custom mounts for project files (projects) and Apache virtual hosts (vhosts)
    config.vm.synced_folder "projects", "/var/www/vhosts", type: "nfs"
    config.vm.synced_folder "vhosts", "/etc/httpd/conf/vhosts", type: "nfs"
    # Disable the default vagrant mount
    config.vm.synced_folder ".", "/vagrant", disabled: true

    # Make sure Apache and MySQL are running when you boot
    config.vm.provision "shell", inline: "service httpd restart && service mysqld restart", run: "always"

end
