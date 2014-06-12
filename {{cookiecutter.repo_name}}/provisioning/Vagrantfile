# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Using Vagrant Cloud
  # https://vagrantcloud.com/ubuntu/trusty64
  config.vm.box = "ubuntu/trusty64"

  config.vm.network :forwarded_port, guest: 80, host: 8080
  config.vm.network :forwarded_port, guest: 4567, host: 4567, id: "redmon"
  config.vm.network :forwarded_port, guest: 8000, host: 8000, id: "django"
  config.vm.network :forwarded_port, guest: 15672, host: 15672, id: "rabbitmq-management"

  config.vm.synced_folder ".", "/vagrant", id: "vagrant-root", disabled: true
  # Uncomment to sync project files to Vagrant, *remember* to change project_name!
  # config.vm.synced_folder "project_name", "/var/www/django/project_name/", id: "django-root", group: "www-data", disabled: false, :mount_options => ["uid=1002"]

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "512"]
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbooks/site.yml"
    ansible.inventory_path = "inventory/local"
  end
end
