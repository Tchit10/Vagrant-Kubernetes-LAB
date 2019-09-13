$script = <<SCRIPT
sudo cp /home/vagrant/kubernetes.repo /etc/yum.repos.d/kubernetes.repo
sudo cp /home/vagrant/k8s.conf /etc/sysctl.d/k8s.conf
sudo yum update -y
SCRIPT

$script2 = <<SCRIPT
sudo swapoff -a
sudo sed -i 's/swapfile/#swapfile/' /etc/fstab
sudo setenforce 0
sudo sed -i 's/^SELINUX=enforcing$/SELINUX=permissive/' /etc/selinux/config
sudo yum install -y git kubelet kubeadm kubectl --disableexcludes=kubernetes
sudo systemctl enable --now kubelet
sudo sysctl --system
SCRIPT

Vagrant.configure("2") do |config|
  
  config.vm.define "vm1" do |vm1|
    vm1.vm.provider :hyperv do |hyperv|
	  hyperv.vmname = "vm1"
	  hyperv.memory = 2048
	  hyperv.cpus = 2
	end
	vm1.vm.box = "centos/7"
	vm1.vm.hostname = "vm1"
	vm1.vm.network "private_network", bridge: "Swisscom"
	vm1.vm.provision "file", source: "kubernetes.repo", destination: "/home/vagrant/kubernetes.repo"
	vm1.vm.provision "file", source: "k8s.conf", destination: "/home/vagrant/k8s.conf"
	vm1.vm.provision "shell", inline: $script
	vm1.vm.provision "docker"
	vm1.vm.provision "shell", inline: $script2
  end
  
  config.vm.define "vm2" do |vm2|
    vm2.vm.provider :hyperv do |hyperv|
	  hyperv.vmname = "vm2"
	  hyperv.memory = 1024
	  hyperv.cpus = 1
	end
	vm2.vm.box = "centos/7"
	vm2.vm.hostname = "vm2"
	vm2.vm.network "private_network", bridge: "Swisscom"
	vm2.vm.provision "file", source: "kubernetes.repo", destination: "/home/vagrant/kubernetes.repo"
	vm2.vm.provision "file", source: "k8s.conf", destination: "/home/vagrant/k8s.conf"
	vm2.vm.provision "shell", inline: $script
	vm2.vm.provision "docker"
	vm2.vm.provision "shell", inline: $script2
  end
  
  config.vm.define "vm3" do |vm3|
	vm3.vm.provider :hyperv do |hyperv|
	  hyperv.vmname = "vm3"
	  hyperv.memory = 1024
          hyperv.cpus = 1
	end
	vm3.vm.box = "centos/7"
	vm3.vm.hostname = "vm3"
	vm3.vm.network "private_network", bridge: "Swisscom"
	vm3.vm.provision "file", source: "kubernetes.repo", destination: "/home/vagrant/kubernetes.repo"
	vm3.vm.provision "file", source: "k8s.conf", destination: "/home/vagrant/k8s.conf"
	vm3.vm.provision "shell", inline: $script
	vm3.vm.provision "docker"
	vm3.vm.provision "shell", inline: $script2
  end

end
