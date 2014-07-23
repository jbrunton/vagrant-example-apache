Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/precise32"
  config.vm.provision :puppet do |puppet|
    puppet.module_path = "modules"
  end
  config.vm.network :forwarded_port, host: 8080, guest: 80
end
