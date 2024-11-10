# Configuración del Vagrantfile
Vagrant.configure("2") do |config|
    # Selecciona la box a usar
    config.vm.box = "ubuntu/jammy64"
    config.vm.boot_timeout = 1200
  
    # Configura la máquina virtual
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 2
    end
  
    # Redirección de puertos
    config.vm.network "forwarded_port", guest: 80, host: 8080

    # Configura la carpeta compartida con permisos específicos
    config.vm.synced_folder "./html", "/var/www/html", owner: "www-data", group: "www-data", type: "virtualbox"

    # Provisión para instalar y habilitar Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2
      sudo systemctl enable apache2   
      sudo systemctl start apache2    
    SHELL
  end
  