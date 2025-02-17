Vagrant.configure("2") do |config|
  # Configuration de la machine 'webserver'
  config.vm.define "webserver" do |webserver|
    webserver.vm.box = "bento/ubuntu-22.04"
    webserver.vm.box_check_update = false
    webserver.vm.network "forwarded_port", guest: 8086, host: 8086
    webserver.vm.network "private_network", ip: "192.168.33.10"
    webserver.vm.synced_folder "./web", "/var/www/html"
    webserver.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.cpus = 1
      vb.name = "webserver"
      vb.memory = "1024"
    end
  end

  # Configuration de la machine 'db'
  config.vm.define "db" do |db|
    db.vm.box = "bento/ubuntu-22.04"
    db.vm.network "private_network", ip: "192.168.33.11"
    #db.vm.synced_folder "./db", "/var/lib/mysql"  # Ajoute un dossier synchronisé pour MySQL (facultatif)
    db.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.cpus = 1
      vb.name = "db"
      vb.memory = "1024"  # Augmente la mémoire pour une meilleure performance
    end
  end
end
