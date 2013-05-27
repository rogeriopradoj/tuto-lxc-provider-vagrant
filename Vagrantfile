Vagrant.configure("2") do |config|
  config.vm.box = "quantal64"
 
  config.vm.define :vbox do |vbox_config|
    vbox_config.vm.network :forwarded_port, guest: 3000, host: 3001
    config.vm.synced_folder "~/.vagrant.d/boxes/quantal64", "/quantal64", id: "vagrant-quantal64"
 
    vbox_config.vm.provision :shell, inline:
      # vagrant-lxc required dependencies and vagrant itself
      'sudo apt-get update -y && sudo apt-get install -y redir lxc &&
      wget -q http://files.vagrantup.com/packages/7e400d00a3c5a0fdf2809c8b5001a035415a607b/vagrant_1.2.2_x86_64.deb -O /tmp/vagrant.deb &&
      sudo dpkg -i /tmp/vagrant.deb && vagrant plugin install vagrant-lxc && cp -rf /quantal64 ~/.vagrant.d/boxes/'
  end
 
  config.vm.define :lxc do |lxc_config|
    lxc_config.vm.network :forwarded_port, guest: 80, host: 3000
    lxc_config.vm.provision :shell, inline:
      'echo "Replace this with your puppet manifests"'
  end
end