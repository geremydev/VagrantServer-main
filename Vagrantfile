Vagrant.configure("2") do |config|
    # Usar una imagen base de Ubuntu
    config.vm.box = "ubuntu/bionic64"
    
    # Asignar una IP estática
    config.vm.network "private_network", type: "dhcp", ip: "192.168.33.10"
    
    # Asignar 512MB de RAM y 1 CPU
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
    
    # Compartir el directorio local con la máquina virtual
    config.vm.synced_folder "./pagina_web", "/var/www/html"
    
    # Configurar el provisioning para instalar Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt update
      sudo apt install -y apache2
      sudo systemctl enable apache2
      sudo systemctl start apache2
    SHELL
  end
  