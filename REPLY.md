Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.provider "virtualbox" do |vb|
  configure.vm.provision :shell, path: "bootstrap.sh"
  config.vm.network "forwarded_port", guest: 8080, host: 80443, host_ip: "192.168.33.10"
  config.vm.provision "shell", inline: <<-SHELL
  apt-get update
  apt-get install -y nginx
  service nginx start
  SHELL
end