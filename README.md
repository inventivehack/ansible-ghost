# Ansible playbook - Ghost

This project contains an [Ansible playbook](http://docs.ansible.com/ansible/playbooks.html) used
for provisioning an Ubuntu 14.04 LTS server with the following characteristics:

* **NGINX** as the web server
* **PostgreSQL** as the DB engine.
* **Mailgun** as the email service provider.
* **Upstart** service for keeping the blog up and running.
* **HTTPS/SSL** configuration ready to go.

## Usage

These instructions will get you a deployable Ansible playbook that you can easily 
use for provisioning any Ubuntu server.

### Prerequisites & Assumptions

You must have [Ansible installed in your computer](http://docs.ansible.com/ansible/intro_installation.html) 
as well as an Ubuntu 14.04 LTS server with ssh public authentication enabled on it. You can easily create 
a public virtual server on any of the following services:

* [Amazon Web Services](https://aws.amazon.com/)
* [Digital Ocean](https://www.digitalocean.com/)
* [Rackspace](https://www.rackspace.com/)

If you don't want to spend any cent by using this playbook, you can test it 
using a virtual machine. We've used a Vagrant for the testing and development of this playbook, 
this is how our *Vagrantfile* looks like:

```
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "public_network"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end
end
```

You can get yours by simply running `vagrant up` after creating you _Vagrantfile_:

### How to use

1. Set up your [inventory](http://docs.ansible.com/ansible/intro_inventory.html)
 by creating a file name `inventory` (_without any extension_) in the root of the project. i.e: 

 ```
 [default]
 10.15.42.4
 10.15.42.3
 ...
 ```

2. Make the [play](play) file an executable one:
 ```
 chmod +x play
 ```

3. Set up the [variables](group_vars)
4. Run:

 ```
 ./play
 ```

### SSL/HTTPS support

Please refer to the [vars](group_vars) section for more information.

## Third party libraries/roles

* [nodesource.node](https://github.com/nodesource/ansible-nodejs-role) - NodeJS installation role

## Not Exactly What You Want?

This is what we use internally. It might not be what you want.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

## What's next for the project?

* Multiple DB engines support:
    * MySQL
    * sqlite3

* Let's encrypt integration for valid SSL certificates generation.
