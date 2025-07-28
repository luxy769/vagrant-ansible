Vagrant.configure("2") do |config|
  # Общие настройки
  config.vm.box = "debian/bookworm64"

  # Хосты
  {
    "web" => "192.168.56.10",
    "app" => "192.168.56.11",
    "monitoring" => "192.168.56.12"
  }.each do |name, ip|
    config.vm.define name do |node|
      node.vm.hostname = name
      node.vm.network "private_network", ip: ip
      node.vm.provider "virtualbox" do |vb|
        vb.memory = 512
        vb.cpus = 1
      end
      node.vm.provision "shell", inline: <<-SHELL
        apt update
        apt install -y python3 sudo
      SHELL
    end
  end
end
