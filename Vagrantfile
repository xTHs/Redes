# Define o Vagrantfile para subir 2 VMs com serviços configurados
Vagrant.configure("2") do |config|
  # Configuração global
  config.vm.box = "ubuntu/focal64" # Ubuntu 20.04

  # -------------------------
  # Máquina 1: Servidor Principal
  # -------------------------
  config.vm.define "server1" do |server1|
    server1.vm.hostname = "server1"
    server1.vm.network "private_network", ip: "192.168.56.10"

    server1.vm.provision "shell", inline: <<-SHELL
      # Atualização de pacotes
      apt-get update && apt-get upgrade -y

      # Instalação dos serviços
      apt-get install -y apache2 isc-dhcp-server bind9 nfs-kernel-server

      # Configuração do Apache
      echo "<h1>Servidor Apache em Server1</h1>" > /var/www/html/index.html
      systemctl enable apache2
      systemctl restart apache2

      # Configuração básica do DHCP
      cat <<EOF > /etc/dhcp/dhcpd.conf
      default-lease-time 600;
      max-lease-time 7200;
      authoritative;

      subnet 192.168.56.0 netmask 255.255.255.0 {
        range 192.168.56.20 192.168.56.30;
        option routers 192.168.56.1;
        option domain-name-servers 192.168.56.10;
      }
      EOF
      systemctl enable isc-dhcp-server
      systemctl restart isc-dhcp-server

      # Configuração básica do DNS (Bind9)
      cat <<EOF > /etc/bind/named.conf.options
      options {
        directory "/var/cache/bind";
        forwarders { 8.8.8.8; 8.8.4.4; };
        dnssec-validation auto;
        listen-on { 192.168.56.10; };
        allow-query { any; };
      };
      EOF
      systemctl enable bind9
      systemctl restart bind9

      # Configuração do NFS
      mkdir -p /srv/nfs_share
      echo "/srv/nfs_share 192.168.56.0/24(rw,sync,no_root_squash)" > /etc/exports
      exportfs -a
      systemctl enable nfs-kernel-server
      systemctl restart nfs-kernel-server
    SHELL
  end

  # -------------------------
  # Máquina 2: Servidor Secundário
  # -------------------------
  config.vm.define "server2" do |server2|
    server2.vm.hostname = "server2"
    server2.vm.network "private_network", ip: "192.168.56.11"

    server2.vm.provision "shell", inline: <<-SHELL
      # Atualização de pacotes
      apt-get update && apt-get upgrade -y

      # Instalação do serviço FTP
      apt-get install -y vsftpd nfs-common

      # Configuração básica do FTP
      cat <<EOF > /etc/vsftpd.conf
      listen=YES
      anonymous_enable=YES
      local_enable=YES
      write_enable=YES
      chroot_local_user=YES
      listen_address=192.168.56.11
      EOF
      systemctl enable vsftpd
      systemctl restart vsftpd

      # Montagem do compartilhamento NFS
      mkdir -p /mnt/nfs_share
      mount -t nfs 192.168.56.10:/srv/nfs_share /mnt/nfs_share
      echo "192.168.56.10:/srv/nfs_share /mnt/nfs_share nfs defaults 0 0" >> /etc/fstab
    SHELL
  end
end
