Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  # Redireccionar el puerto 8080 de la máquina virtual al puerto 8080 del host
  config.vm.network "forwarded_port", guest: 80, host: 8080

  # Instalar Ansible en la máquina virtual
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y software-properties-common
    sudo apt-add-repository --yes --update ppa:ansible/ansible
    sudo apt-get install -y ansible
  SHELL

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    # Ruta del archivo de inventario de Ansible
    ansible.inventory_path = "inventory"
  end
end