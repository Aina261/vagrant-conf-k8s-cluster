# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_NO_PARALLEL'] = 'yes'

Vagrant.configure(2) do |config|

  # config.vm.provision "shell", path: "bootstrap.sh"

  # Kubernetes Master Server
  config.vm.define "k8s-master" do |k8smaster|
    k8smaster.vm.box = "centos/7"
    k8smaster.vm.hostname = "k8s-master.dns.com"
    k8smaster.vm.network "private_network", ip: "192.0.0.100"
    k8smaster.vm.provider "virtualbox" do |v|
      v.name = "k8s-master"
      v.memory = 2048
      v.cpus = 2
    end
    # k8s-master.vm.provision "shell", path: "bootstrap_kmaster.sh"
  end

  NodeCount = 4

  # Kubernetes Worker Nodes
  (1..NodeCount).each do |i|
    config.vm.define "k8s-worker-#{i}" do |k8sworker|
      k8sworker.vm.box = "centos/7"
      k8sworker.vm.hostname = "kworker#{i}.example.com"
      k8sworker.vm.network "private_network", ip: "192.0.0.10#{i}"
      k8sworker.vm.provider "virtualbox" do |v|
        v.name = "k8s-worker-#{i}"
        v.memory = 2048
        v.cpus = 2
      end
      # k8s-worker.vm.provision "shell", path: "bootstrap_kworker.sh"
    end
  end

end

