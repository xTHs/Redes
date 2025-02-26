# 📚 Administração de Redes de Computadores - Trabalho Final

Bem-vindo ao repositório oficial do projeto final da disciplina **Administração de Redes de Computadores - 2024**! 📁

Este repositório reúne todos os arquivos e scripts necessários para configurar os serviços de rede utilizados no projeto, proporcionando uma solução prática e funcional para os desafios propostos na disciplina. Aqui, você encontrará as instruções e configurações detalhadas para cada serviço implementado.


## 🚀 Primeiros Passos

Para começar a usar os serviços de rede deste projeto, você precisará instalar o Vagrant e o VirtualBox. Siga os passos abaixo para garantir que tudo seja configurado corretamente:

1. **💾 Instalação do Vagrant**

   O Vagrant é uma ferramenta essencial para gerenciar máquinas virtuais através de uma única interface de linha de comando. Para instalar o Vagrant, acesse:
   
   - [Guia de Instalação do Vagrant](https://www.vagrantup.com/docs/installation)

2. **📦 Instalação do VirtualBox**

   O VirtualBox permite a criação e gerenciamento de máquinas virtuais hospedadas. Para instalá-lo, visite:
   
   - [Downloads do VirtualBox](https://www.virtualbox.org/wiki/Downloads)

Após a instalação de ambos, você estará pronto para configurar e executar os ambientes virtuais necessários para este projeto.


3. **🔗 Clonando o Repositório**

   Para obter uma cópia local dos scripts e arquivos de configuração necessários, clone o repositório usando o seguinte comando no terminal:
   ```bash
   git clone https://github.com/xTHs/Redes.git



4. **🚀 Subindo os Serviços**

   Com o Vagrant e o VirtualBox instalados e o repositório clonado, você está pronto para inicializar as máquinas virtuais configuradas. Certifique-se de estar no diretório raiz do repositório, onde se encontra o arquivo `Vagrantfile`. Execute o seguinte comando no terminal para iniciar todas as máquinas virtuais definidas no Vagrantfile:
   ```bash
   vagrant up


5. **🛠️ Executando o Arquivo de Provisão**

   Após iniciar as máquinas virtuais com `vagrant up`, o Vagrant automaticamente executará o [arquivo de provisão](./provision.sh), que contém os scripts necessários para configurar cada serviço de rede. Este processo pode levar alguns minutos, dependendo da configuração e do número de serviços a serem instalados.

   ✅ Quando todas as configurações estiverem concluídas, você poderá acessar a máquina virtual diretamente através do terminal. Para se conectar via SSH à máquina chamada `server1`, utilize o comando abaixo. Este comando estabelece uma conexão direta com o servidor `server1`, que foi o nome escolhido para esta instância no projeto Vagrant. Lembre-se de que o nome do servidor é configurável e pode ser alterado conforme suas preferências no `Vagrantfile`.
   
   
   ```bash
   vagrant ssh server1
   
6. **🌐Acesso SSH ao Servidor `server1`**

Após estabelecer a conexão SSH com o servidor `server1` utilizando o comando `vagrant ssh server1`, você terá acesso total ao ambiente de linha de comando do servidor. Isso permite executar uma variedade de tarefas administrativas, tais como:

- **Instalar software adicional**: Para expandir as funcionalidades do servidor ou atender requisitos específicos de sua aplicação.
- **Modificar configurações de sistema**: Ajustar configurações para otimizar o desempenho ou adaptar o ambiente às suas necessidades.
- **Verificar o status de serviços**: Monitorar e gerenciar os serviços em execução na máquina para garantir que tudo está funcionando como esperado.

Utilizar a conexão SSH é fundamental para administrar eficientemente a máquina virtual, permitindo-lhe maximizar o uso das funcionalidades disponibilizadas pelo Vagrant e pela configuração específica do seu servidor.


<p align="center">
  <img src="IMG/IMG1.jpeg" alt="Descrição da Imagem 1" width="300"/>
</p>

---

## 🛠️ Serviços Configurados

Confira os serviços configurados e aprenda a verificar cada um deles utilizando os comandos apropriados.

- [**DHCP**]-Aloca automaticamente endereços IP e configurações de rede para dispositivos em uma rede.
  ```bash
  sudo systemctl status isc-dhcp-server
- [**DNS**]-Traduz nomes de domínio em endereços IP, facilitando o acesso a websites.
  ```bash
  sudo systemctl status bind9

- [**FTP**]-Permite a transferência de arquivos entre sistemas conectados através de uma rede.
  ```bash
  sudo systemctl status vsftpd

- [**HTTP**]-Protocolo usado para transmitir documentos e dados na World Wide Web.
  ```bash
  sudo systemctl status apache2

- [**NFS**]-Sistema de arquivos de rede que permite o acesso a arquivos sobre uma rede de computadores como se estivessem no disco local.
  ```bash
  sudo systemctl status nfs-kernel-server


---

### 🌐 **DHCP** (Dynamic Host Configuration Protocol)

O **DHCP** desempenha um papel crucial na administração de redes ao automatizar a distribuição de endereços IP e outras configurações de rede essenciais. Esse protocolo elimina a necessidade de configuração manual de cada dispositivo conectado à rede, agilizando a conexão de novos dispositivos e garantindo a gestão eficiente do espaço de endereçamento IP.


---

### 🌍 **DNS** (Domain Name System)

O **DNS** é fundamental para a funcionalidade da internet, atuando como o tradutor entre os endereços de nomes de domínio que os humanos usam (como `www.example.com`) e os endereços IP que os computadores utilizam para se comunicar. Este serviço garante que os usuários possam acessar websites de forma rápida e intuitiva, simplificando a navegação na web ao eliminar a necessidade de memorizar sequências numéricas complexas.


---

### 📁 **FTP** (File Transfer Protocol)

O **FTP** é um protocolo essencial para transferir arquivos entre sistemas conectados à internet. Ele facilita tanto o upload quanto o download de arquivos em servidores remotos, oferecendo uma solução eficaz para a gestão de dados digitais em grande escala. Esse protocolo é amplamente utilizado por administradores de sistemas, desenvolvedores e usuários que necessitam de uma transferência de arquivos confiável e organizada.


---

### 🌐 **Apache HTTP Server**

O **Apache HTTP Server** é um servidor web robusto e amplamente utilizado, conhecido por sua versatilidade e força em hospedar websites e aplicações web. Ele suporta uma variedade de módulos que expandem suas funcionalidades, incluindo processamento de PHP, proxy reverso, e muito mais. O Apache é ideal para ambientes que exigem configuração customizada e é uma escolha popular em muitas empresas de grande porte devido à sua comprovada estabilidade e escalabilidade.


---

### 💻 **NFS** (Network File System)

O **NFS** é um protocolo destinado ao compartilhamento remoto de sistemas de arquivos entre computadores em uma rede. Com o NFS, arquivos armazenados em um servidor podem ser acessados por máquinas clientes como se estivessem localizados em seus próprios discos locais. Este protocolo é essencial para ambientes que necessitam de acesso fácil e rápido a dados centralizados, facilitando a colaboração e a eficiência operacional.


---

## 🔗 Links Úteis

Aqui estão alguns recursos essenciais que podem ajudar no desenvolvimento e gerenciamento dos serviços configurados no seu projeto:

- 📦 **Vagrant**: Explore a [Documentação Oficial do Vagrant](https://www.vagrantup.com/docs) para aprender mais sobre como configurar e utilizar este gerenciador de máquinas virtuais.
- 🌐 **Apache HTTP Server**: Acesse a [Documentação Oficial do Apache](https://httpd.apache.org/docs/) para obter informações detalhadas sobre configuração, segurança e otimização do servidor web.
- 🌍 **DNS**: Consulte a [Documentação Oficial do DNS na ISC](https://www.isc.org/bind/) para instruções sobre a configuração e utilização do serviço de resolução de nomes.
- 💻 **NFS (Network File System)**: Acesse a [Documentação Oficial do NFS no site da Red Hat](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/storage_administration_guide/ch-nfs) para aprender a configurar e usar sistemas de arquivos compartilhados em rede.
- 📁 **FTP (File Transfer Protocol)**: Confira a [Documentação Oficial do FTP na Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview) para orientações sobre transferência de arquivos entre sistemas.
- 🌐 **DHCP (Dynamic Host Configuration Protocol)**: Consulte a [Documentação Oficial do DHCP no site da Microsoft](https://docs.microsoft.com/en-us/windows-server/networking/technologies/dhcp/dhcp-top) para aprender a configurar a distribuição dinâmica de endereços IP na rede.


---

## 📝 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](./LICENSE) para mais detalhes.

---

👨‍💻 Desenvolvido por:

- Thiago Silva
- Mário Alves


