# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANT_API_VERSION = "2"
VAGRANT_VIRTUAL_BOX = "ubuntu/focal64"

$apt_update = <<APT_UPDATE_ENDSCRIPT
sudo apt-get update --yes
sudo apt-get upgrade --yes
APT_UPDATE_ENDSCRIPT

$install_docker = <<INSTALL_DOCKER_ENDSCRIPT
sudo apt-get install ca-certificates curl gnupg lsb-release --yes
sudo mkdir -m 0755 -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update --yes
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin docker-compose --yes
sudo apt-get install gnupg2 pass --yes
sudo usermod -a -G docker vagrant
INSTALL_DOCKER_ENDSCRIPT

$install_minikube = <<INSTALL_MINIKUBE_ENDSCRIPT
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
INSTALL_MINIKUBE_ENDSCRIPT

Vagrant.configure(VAGRANT_API_VERSION) do |config|
  config.vm.box = VAGRANT_VIRTUAL_BOX
  config.vm.provider "virtualbox" do |vbox|
    vbox.memory = 4096
	vbox.cpus = 2
  end
  config.vm.provision "shell", inline: $apt_update
  config.vm.provision "shell", inline: $install_docker
  config.vm.provision "shell", inline: $install_minikube
  config.vm.provision "file", source: ".bash_aliases", destination: ".bash_aliases"
end