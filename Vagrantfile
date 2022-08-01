Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-20.04"
  config.vm.synced_folder "./", "/home/vagrant/work", create:"true"
  config.vm.network "forwarded_port", guest: 8000, host: 8000
  
  config.vm.provision "shell", inline: <<-SHELL
    apt update
    apt -y upgrade
    apt install -y tree
    apt install -y python3-pip
    pip install Django
    pip install -U channels
    pip install channels_redis
    pip install django-bootstrap5
    
    # install docker
    apt-get update
    apt-get install \
      ca-certificates \
      curl \
      gnupg \
      lsb-release
    mkdir -p /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    echo \
      "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
      $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    apt-get update
    apt-get install -y docker-ce docker-ce-cli containerd.io docker-compose-plugin
    apt-get install -y docker-ce=5:20.10.17~3-0~ubuntu-focal docker-ce-cli=5:20.10.17~3-0~ubuntu-focal containerd.io docker-compose-plugin
  SHELL
end
