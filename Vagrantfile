Vagrant.configure(2) do |config|
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.network "private_network", ip: "192.168.10.2"
  #To use the Django webserver, forward some extra ports 
  config.vm.network "forwarded_port", guest: 8000, host: 8001

  config.vm.synced_folder "./webapps", "/vagrant/webapps", id: "webroot",
    owner: "vagrant",
    group: "www-data",
    mount_options: ["dmode=777,fmode=776"]

  # Add vagrant to www-data, for access to /webapps
  config.vm.provision "shell",
    inline: "usermod -a -G vagrant www-data"

  # ssh settings
  config.ssh.insert_key = false
  config.ssh.private_key_path = ["keys/ansible_key", "~/.vagrant.d/insecure_private_key"]
  config.vm.provision "file", source: "keys/ansible_key.pub", destination: "~/.ssh/authorized_keys"
  config.vm.provision "shell", inline: <<-EOC
    sudo sed -i -e "\\#PasswordAuthentication yes# s#PasswordAuthentication yes#PasswordAuthentication no#g" /etc/ssh/sshd_config
    sudo service ssh restart
  EOC
end