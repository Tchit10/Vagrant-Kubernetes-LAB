$script = <<SCRIPT
sudo cp /home/vagrant/nerootca2042.crt /etc/pki/ca-trust/source/anchors/nerootca2042.crt
sudo update-ca-trust extract
sudo yum update
sudo swapoff -a
sudo sed -i '/ swap / s/^\(.*\)$/#\1/g' /etc/fstab
SCRIPT

Vagrant.configure("2") do |config|
  
  config.vm.define "vm1" do |vm1|
    vm1.vm.provider :hyperv do |hyperv|
	  hyperv.vmname = "vm1"
	end
	vm1.vm.box_download_ca_cert = "nerootca2042.crt"
	vm1.vm.box = "centos/7"
	vm1.vm.hostname = "vm1"
	vm1.vm.network "private_network", bridge: "Interne Partagé avec VLL_SI_CGI"
	vm1.vm.provision "file", source: "nerootca2042.crt", destination: "/home/vagrant/nerootca2042.crt"
	vm1.vm.provision "file", source: "kubernetes.repo", destination: "/etc/yum.repos.d/kubernetes.repo"
	vm1.vm.provision "shell", inline: $script
	vm1.vm.provision "docker"
  end
  
  config.vm.define "vm2" do |vm2|
    vm2.vm.provider :hyperv do |hyperv|
	  hyperv.vmname = "vm2"
	end
	vm2.vm.box_download_ca_cert = "nerootca2042.crt"
	vm2.vm.box = "centos/7"
	vm2.vm.hostname = "vm2"
	vm2.vm.network "private_network", bridge: "Interne Partagé avec VLL_SI_CGI"
	vm2.vm.provision "file", source: "nerootca2042.crt", destination: "/home/vagrant/nerootca2042.crt"
	vm2.vm.provision "shell", inline: $script
	vm2.vm.provision "docker"
  end
  
  config.vm.define "vm3" do |vm3|
	vm3.vm.provider :hyperv do |hyperv|
	  hyperv.vmname = "vm3"
	end
	vm3.vm.box_download_ca_cert = "nerootca2042.crt"
	vm3.vm.box = "centos/7"
	vm3.vm.hostname = "vm3"
	vm3.vm.network "private_network", bridge: "Interne Partagé avec VLL_SI_CGI"
	vm3.vm.provision "file", source: "nerootca2042.crt", destination: "/home/vagrant/nerootca2042.crt"
	vm3.vm.provision "shell", inline: $script
	vm3.vm.provision "docker"
  end

end
