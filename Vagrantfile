Vagrant.configure("2") do |config|

    config.vm.define "BBDD" do |nodo1|

        nodo1.vm.box = "ubuntu/trusty64"

        nodo1.vm.hostname = "servidorBBDD"
        nodo1.vm.provider "virtualbox" do |v|

          v.name = "BBDD"
          v.memory = "2048"
          v.cpus = 2


        end
        nodo1.vm.network "forwarded_port", guest: 3306, host: 33060
        nodo1.vm.network "private_network", ip: "192.168.56.31"
        nodo1.vm.provision "shell", path: "scripts/nodo1.sh", privileged: "true"
        nodo1.vm.provision "shell" do |s|
          ssh_pub_key = File.readlines("/home/ciber2/.ssh/id_rsa.pub").first.strip
             s.inline = <<-SHELL
                echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
                echo #{ssh_pub_key} >> /root/.ssh/authorized_keys
                SHELL
        end
        

    end

    config.vm.define "web" do |nodo2|

      nodo2.vm.box = "ubuntu/trusty64"

     
      nodo2.vm.hostname = "servidorWeb"
      nodo2.vm.network "forwarded_port", guest: 80, host: 8080
      nodo2.vm.network "private_network", ip: "192.168.56.32"
      nodo2.vm.provision "shell", path: "scripts/nodo2.sh", privileged: "true"
      nodo2.vm.provision "shell" do |s|
        ssh_pub_key = File.readlines("/home/ciber2/.ssh/id_rsa.pub").first.strip
           s.inline = <<-SHELL
              echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
              echo #{ssh_pub_key} >> /root/.ssh/authorized_keys
              SHELL
      end

      nodo2.vm.provider "virtualbox" do |v|

        v.name = "WEB"
        v.memory = "1024"
        v.cpus = 2


      end


    end

    config.vm.define "web2" do |nodo3|

      nodo3.vm.box = "ubuntu/trusty64"

      nodo3.vm.provider "virtualbox" do |v|

        v.name = "WEB2"
        v.memory = "2048"
        v.cpus = 2


      end
      nodo3.vm.hostname = "servidorWeb2"
      nodo3.vm.network "forwarded_port", guest: 80, host: 9090
      nodo3.vm.network "private_network", ip: "192.168.56.33"
      nodo3.vm.provision "shell", path: "scripts/nodo3.sh", privileged: "true"
      nodo3.vm.provision "shell" do |s|
        ssh_pub_key = File.readlines("/home/ciber2/.ssh/id_rsa.pub").first.strip
           s.inline = <<-SHELL
              echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys
              echo #{ssh_pub_key} >> /root/.ssh/authorized_keys
              SHELL
      end

    end

  end