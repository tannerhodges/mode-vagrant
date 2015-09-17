# MODE Vagrant 3.0.0

## Quick start

```
vagrant up
```

## First time using Vagrant?

- Install VirtualBox and Vagrant via [Homebrew](http://brew.sh/):
  - `brew cask install virtualbox`
  - `brew cask install vagrant`
- Go to this directory in your Terminal app and run `vagrant up`.
- Add project files to `projects`. For example:
  - `cd projects/clients/`
  - `git clone git@github.com:madebymode/boars-head-website.git`
- Setup Apache virtual hosts for each project in `vhosts`.
  - You can copy `vhosts/example.conf` as a reference.

TODO: How to setup local host domains.

## Testing on mobile devices

- In the `Vagrantfile`, make sure `public_network` is set to the device that you're connected to the Internet with.
  - For example, if you're using a wifi connection then `:bridge` should be set to `"en1: Wi-Fi (AirPort)"`
- Find the vhost `.conf` file for the site you want to share and make sure it's the only file in `vhosts/default/`.
- `vagrant ssh`
- Restart Apache with `sudo service httpd restart`
- Run `ifconfig eth2` to find which IP address to use.
  - Look for the `inet addr`, which should be something like `192.168.1.123`
- Visit that IP in a browser on any other device connected to the same network and you should see your site.

---

## Helpful Commands

```
ifconfig                      # How's my network configured?
sudo service httpd restart    # Restart Apache
sudo service mysqld restart   # Restart MySQL
sudo yum update -y            # Update all my CentOS packages + dependencies
cat /etc/redhat-release       # Which version of CentOS am I running?
```

## Server Specs

- Box based on [CentOS 6.7 i386 Minimal (VirtualBox Guest Additions 4.3.26)](https://dl.dropboxusercontent.com/u/51478659/vagrant/morungos-centos67.box)
  - Listed on [Vagrantbox.es](http://www.vagrantbox.es/)
- CentOS 6.7
- PHP 5.6
- MySQL 5.5

TODO: Included PHP packages and config.


