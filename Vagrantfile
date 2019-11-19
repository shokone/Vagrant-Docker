$install_docker = <<SCRIPT
echo "Installing Docker..."
curl -sSL https://get.docker.com/ | sh
usermod -aG docker vagrant
apt-get install docker-compose -y
SCRIPT

$create_bastion = <<SCRIPT
echo "Download some images..."
docker pull hello-world
docker pull centos:7
docker pull ubuntu
docker pull alpine
docker pull nginx
docker pull httpd
docker pull tomcat
docker pull mysql:5.6
docker pull docker.io/anchore/anchore-engine
echo "Download and create anchore-engine with docker-compose..."
cd /home/vagrant/aevolume
docker-compose pull
echo "Download docker-bench-security..."
cd /home/vagrant/
git clone https://github.com/docker/docker-bench-security.git
SCRIPT

Vagrant.configure('2') do |config|

  vm_box = 'ubuntu/xenial64'

  config.vm.define :bastion, primary: true  do |bastion|
    bastion.vm.box = vm_box
    bastion.vm.box_check_update = true
    bastion.vm.network :private_network, ip: "10.100.1.200"
    bastion.vm.network :forwarded_port, guest: 8080, host: 8080
    bastion.vm.network :forwarded_port, guest: 5000, host: 5000
    bastion.vm.hostname = "bastion"
    bastion.vm.synced_folder ".", "/vagrant"
    bastion.vm.provision "shell", inline: $install_docker, privileged: true
    bastion.vm.provision "shell", inline: $create_bastion, privileged: true
    bastion.vm.synced_folder "aevolume", "/home/vagrant/aevolume"
    bastion.vm.provider "virtualbox" do |vb|
      vb.name = "bastion"
      vb.memory = "4096"
    end
  end

end
