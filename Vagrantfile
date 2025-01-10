Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64" # Ubuntu 20.04

  # -------------------------
  # Máquina 1: Servidor Principal
  # -------------------------
  config.vm.define "server1" do |server1|
    server1.vm.hostname = "server1"
    server1.vm.network "private_network", ip: "192.168.56.10"

    # Monta os diretórios locais na VM
    server1.vm.synced_folder "./Apache", "/etc/apache2"
    server1.vm.synced_folder "./DHCP", "/etc/dhcp"
    server1.vm.synced_folder "./DNS", "/etc/bind"
    server1.vm.synced_folder "./NFS", "/etc/exports"

    # Script para iniciar os serviços
    server1.vm.provision "shell", inline: <<-SHELL
      systemctl restart apache2
      systemctl restart isc-dhcp-server
      systemctl restart bind9
      systemctl restart nfs-kernel-server
    SHELL
  end

  # -------------------------
  # Máquina 2: Servidor Secundário
  # -------------------------
  config.vm.define "server2" do |server2|
    server2.vm.hostname = "server2"
    server2.vm.network "private_network", ip: "192.168.56.11"

    # Monta os diretórios locais na VM
    server2.vm.synced_folder "./FTP", "/etc/vsftpd"
    server2.vm.synced_folder "./IMG", "/var/ftp/pub"

    # Script para iniciar os serviços
    server2.vm.provision "shell", inline: <<-SHELL
      systemctl restart vsftpd
    SHELL
  end
end
