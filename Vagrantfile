Vagrant.configure("2") do |config|
    # Usar una imagen base de Ubuntu
    config.vm.box = "ubuntu/bionic64"
  
    # Asignar 512MB de RAM y 1 CPU
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  
    # Configurar el puerto del servidor web (Apache)
    config.vm.network "forwarded_port", guest: 80, host: 8080
  
    # Configurar un directorio compartido entre la máquina local y la VM
    config.vm.synced_folder "./pagina_web", "/var/www/html"
  
    # Ejecutar comandos para instalar Apache en la máquina virtual
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo systemctl enable apache2
      sudo systemctl start apache2
    SHELL
  end
  