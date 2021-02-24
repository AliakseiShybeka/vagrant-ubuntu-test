Vagrant.configure("2") do |config|

  
  # не копировать приват ключ в хостовую машину
  
   
  # # изменить объем памяти для виртуальной машины по умолчанию
   config.vm.provider :virtualbox do |vb|
    config.ssh.insert_key = false
    vb.customize ["modifyvm", :id, "--memory", "2048"]
   # config.vm.synced_folder "./", "/vagrant"
   end

  # Application server 1
  config.vm.define "app1" do |app|
    app.vm.hostname = "orc-app1.dev"
    app.vm.box = "geerlingguy/centos7"
    app.vm.network :private_network, ip: "192.168.60.4"
    config.vm.provision "shell", path: "/provision/centos_provision.sh"
  end

       # Application server 2
   config.vm.define "db" do |db|
     db.vm.hostname = "orc-db.dev"
     db.vm.box = "hashicorp/bionic64"
     db.vm.network :private_network, ip: "192.168.60.5"
   end

    # # Provision configuration for Ansible
    # config.vm.provision  :ansible do |ansible|
    #   ansible.playbook = "playbook.yml"
    #   ansible.become = true
    #  end 

end