# Configuração principal do Vagrant para a versão 2
Vagrant.configure("2") do |config|
    
    # Loop para criar a máquina master
    (1..1).each do |i|
        # Define a VM "master"
        config.vm.define "master-#{i}" do |k8s|
            # Configura a imagem base para a VM
            k8s.vm.box = "ubuntu/bionic64"
            # Define o nome de host para a VM master
            k8s.vm.hostname = "master-#{i}"
            # Configura o IP da rede privada para a VM master
            k8s.vm.network "private_network", ip: "192.168.56.#{i+100}"

            # Configura a chave SSH sem gerar nova chave a cada execução
            k8s.ssh.insert_key = false
            # Define os caminhos para as chaves privadas SSH
            k8s.ssh.private_key_path = ['~/.vagrant.d/insecure_private_key', '~/.ssh/id_rsa']
            # Provisão de chave pública para acesso SSH
            k8s.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"

            # Configuração do provedor VirtualBox
            k8s.vm.provider "virtualbox" do |vb|
                # Define o número de CPUs
                vb.cpus = 2
                # Define a quantidade de memória em MB
                vb.memory = "2048"
            end
        end
    end

    # Loop para criar as máquinas worker
    (1..2).each do |i|
        # Define a VM "worker"
        config.vm.define "worker-#{i}" do |k8s|
            # Configura a imagem base para a VM
            k8s.vm.box = "ubuntu/bionic64"
            # Define o nome de host para cada VM worker
            k8s.vm.hostname = "worker-#{i}"
            # Configura o IP da rede privada para cada VM worker
            k8s.vm.network "private_network", ip: "192.168.56.#{i+200}"

            # Configura a chave SSH sem gerar nova chave a cada execução
            k8s.ssh.insert_key = false
            # Define os caminhos para as chaves privadas SSH
            k8s.ssh.private_key_path = ['~/.vagrant.d/insecure_private_key', '~/.ssh/id_rsa']
            # Provisão de chave pública para acesso SSH
            k8s.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"

            # Configuração do provedor VirtualBox para cada worker
            k8s.vm.provider "virtualbox" do |vb|
                # Define o número de CPUs
                vb.cpus = 1
                # Define a quantidade de memória em MB
                vb.memory = "2048"
            end
        end
    end
end
