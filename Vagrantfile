Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.provider "virtualbox"
  # Sync project folder with the VM.
  # Change the owner so NGINX has permision to serve these files.
  config.vm.synced_folder "../dnd", "/var/www/dnd", owner:'nginx', group: "vagrant"
  config.vm.disk :disk, size: "24GB", primary: true
  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  config.vm.network "public_network", bridge: [
    "en0: Wi-Fi (Wireless)",
    "en1: Wi-Fi (AirPort)",
    "en2: Wi-Fi (AirPort)",
  ]
  config.ssh.insert_key = false
  # Set memory limits
  config.vm.provider "virtualbox" do |v|
    v.name = "ubuntu"
    v.memory = 2048
    v.cpus = 2
  end
  # Ansible is executed on Vagrant host
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.extra_vars = "vars.yaml"
    ansible.galaxy_role_file = "requirements.yaml"
    ansible.galaxy_roles_path = "~/.ansible/roles"
    ansible.config_file = "ansible.cfg"
    ansible.galaxy_command = "ansible-galaxy install --role-file=%{role_file} --roles-path=%{roles_path}"
    ansible.playbook = "playbook.yaml"
  end
end

