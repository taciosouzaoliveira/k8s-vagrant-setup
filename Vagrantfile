Vagrant.configure("2") do |config|
    (1..1).each do |i|
        config.vm.define "master-#{i}" do |k8s|
            k8s.vm.box = "ubuntu/bionic64"
            k8s.vm.hostname = "master-#{i}"
            k8s.vm.network "private_network", ip: "192.168.56.#{i+100}"

            k8s.ssh.insert_key = false
            k8s.ssh.private_key_path = ['~/.vagrant.d/insecure_private_key', '~/.ssh/id_rsa']
            k8s.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"

            k8s.vm.provider "virtualbox" do |vb|
                vb.cpus = 2
                vb.memory = "2048"
            end
        end
    end

    (1..2).each do |i|
        config.vm.define "worker-#{i}" do |k8s|
            k8s.vm.box = "ubuntu/bionic64"
            k8s.vm.hostname = "worker-#{i}"
            k8s.vm.network "private_network", ip: "192.168.56.#{i+200}"

            k8s.ssh.insert_key = false
            k8s.ssh.private_key_path = ['~/.vagrant.d/insecure_private_key', '~/.ssh/id_rsa']
            k8s.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"

            k8s.vm.provider "virtualbox" do |vb|
                vb.cpus = 1
                vb.memory = "2048"
            end
        end
    end
end
