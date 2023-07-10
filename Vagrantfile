Vagrant.configure("2") do |config|
    
    config.vm.box = "centos/stream8"
    config.vm.box_version = "20210210.0"
 
    config.vm.provider :virtualbox do |v|
      v.memory = 2048
      v.cpus = 1
    end
  
    
    boxes = [
      { :name => "ipa.otus.lan",
        :ip => "192.168.56.10",
      },
      { :name => "client1.otus.lan",
        :ip => "192.168.56.11",
      },
      { :name => "client2.otus.lan",
        :ip => "192.168.56.12",
      }
    ]
    
    boxes.each do |opts|
      config.vm.define opts[:name] do |config|
        config.vm.hostname = opts[:name]
        config.vm.network "private_network", ip: opts[:ip]
      end
      config.vm.provision "ansible" do |ansible|
        ansible.playbook = "provisioning/ldap.yml"
        ansible.inventory_path = "ansible/hosts.ini"
        ansible.become = "true"
      end
    end
  end
