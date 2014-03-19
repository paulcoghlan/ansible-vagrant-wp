ansible-vagrant-wp
==================
Deploy a WordPress development environment to your local machine using Vagrant, then deploy dev, test and production instances to EC2 using Ansible.

Deploys Ubuntu 12.04 with MySQL, php-fpm and Nginx.

Based on <https://github.com/Varying-Vagrant-Vagrants/VVV>

##Local Development using Vagrant
1. Install VirtualBox <https://www.virtualbox.org/> and Vagrant <http://www.vagrantup.com/>
1. Install Vagrant hosts updater plugin:
<https://github.com/cogitatio/vagrant-hostsupdater>
1. Provision Ubuntu 12.04 local WP server:
    
     `vagrant up` 
1. Install WordPress using Ansible Playbook:
     
	 `ansible-playbook -i dev cms.yml`
1. Visit running instance at <http://cms.local>           
      
   
## Deploy to EC2
1. Rename aws_private_vars.yml to .aws_private_vars.yml, populate with your AWS access key, secret key and keypair name.  Dot file with your private AWS credentials won't get checked in :-)
1. Provision EC2 instance:

   `ansible-playbook -i dev ec2-provision.yml` 

1. Install WordPress on EC2 instance using Ansible Playbook:

	 `ansible-playbook -i dev cms.yml`           

1. Visit running instance at <http://cms.dev>           


