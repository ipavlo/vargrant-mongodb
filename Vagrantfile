# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.insert_key = false
  config.vm.hostname = "mongoNode"
  config.vm.box = "ubuntu/trusty64"
  config.vm.synced_folder "sync/", "/usr/mongo", create: true
  config.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777", "fmode=666"]
  config.vm.network "private_network", ip: "192.168.77.6"
  config.vm.define "mongodb" do |mongodb|
  end
  config.vm.provider :virtualbox do |vb|
    vb.name = "mongodb"
  end
  config.vm.provision :ansible do |ansible|  
    # Disable default limit to connect to all the machines
    ansible.limit = "all"
    ansible.playbook = "main.yml"
    ansible.verbose = "-vvvv"
    ansible.sudo = true
  end
end
