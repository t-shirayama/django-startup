Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-20.04"
  config.vm.synced_folder "./work", "/home/vagrant/work"
  config.vm.network "forwarded_port", guest: 8000, host: 8000
  
  config.vm.provision "shell", inline: <<-SHELL
    apt update
    apt -y upgrade
    apt install -y python3-pip
    pip install Django
  SHELL
end
