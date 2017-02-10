Vagrant.configure("2") do |config|
  config.vm.provider :virtualbox do |vb, override|
    override.vm.box = "intro-to-vagrant"
    # XXX: Define environment variable VAGRANT_BOX_REPOSITORY_URL.
    # - May be local file:/// or http:// URL.
    override.vm.box_url = "#{ENV['VAGRANT_BOX_REPOSITORY_URL']}/ubuntu-dev-java.box"
    override.ssh.username = "ubuntu"
    override.vm.synced_folder "#{ENV['HOME']}/.ssh", "/ssh"
    override.vm.network "forwarded_port", guest: 8000, host: 8080
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/intro-to-vagrant.yml"
  end
end
