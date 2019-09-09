$script = <<SCRIPT
sudo yum update
sudo swapoff -a
sudo sed -i '/ swap / s/^\(.*\)$/#\1/g' /etc/fstab
SCRIPT

Vagrant.configure("2") do |config|
  
  config.vm.define "vm1" do |vm1|
    vm1.vm.provider :hyperv do |hyperv|
	  hyperv.vmname = "vm1"
	end
	vm1.vm.box = "centos/7"
	vm1.vm.hostname = "vm1"
	vm1.vm.network "private_network", bridge: "Swisscom"
	vm1.vm.provision "shell", inline: $script
	vm1.vm.provision "docker"
  end
  
  config.vm.define "vm2" do |vm2|
    vm2.vm.provider :hyperv do |hyperv|
	  hyperv.vmname = "vm2"
	end
	vm2.vm.box = "centos/7"
	vm2.vm.hostname = "vm2"
	vm2.vm.network "private_network", bridge: "Swisscom"
	vm2.vm.provision "shell", inline: $script
	vm2.vm.provision "docker"
  end
  
  config.vm.define "vm3" do |vm3|
	vm3.vm.provider :hyperv do |hyperv|
	  hyperv.vmname = "vm3"
	end
	vm3.vm.box = "centos/7"
	vm3.vm.hostname = "vm3"
	vm3.vm.network "private_network", bridge: "Swisscom"
	vm3.vm.provision "shell", inline: $script
	vm3.vm.provision "docker"
  end

end
