

Vagrant.configure("2") do |config|
  config.hostmanager.enabled = true
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "256"
  end

  config.vm.define "client" do |client|
    client.vm.box = "velocity42/xenial64"
    client.vm.network :private_network, ip: "192.168.2.9"
    client.vm.hostname = "client"

    client.vm.provision :shell, :inline => <<'EOF'
if [ ! -f "/home/vagrant/.ssh/id_rsa" ]; then
  ssh-keygen -t rsa -N "" -f /home/vagrant/.ssh/id_rsa
fi
cp /home/vagrant/.ssh/id_rsa.pub /vagrant/client.pub

cat << 'SSHEOF' > /home/vagrant/.ssh/config
Host *
  StrictHostKeyChecking no
  UserKnownHostsFile=/dev/null
SSHEOF

chown -R vagrant:vagrant /home/vagrant/.ssh/
EOF
  end

  config.vm.define "controller0" do |controller0|    
    controller0.vm.box = "velocity42/xenial64"
    controller0.vm.hostname = "controller0"
    controller0.vm.network "private_network", ip: "192.168.2.2"
    controller0.vm.provision :shell, inline: 'cat /vagrant/client.pub >> /home/vagrant/.ssh/authorized_keys'
  end

  config.vm.define "controller1" do |controller1|
    controller1.vm.box = "velocity42/xenial64"
    controller1.vm.network :private_network, ip: "192.168.2.3"
    controller1.vm.hostname = "controller1"
    controller1.vm.provision :shell, inline: 'cat /vagrant/client.pub >> /home/vagrant/.ssh/authorized_keys'
  end

  config.vm.define "controller2" do |controller2|
    controller2.vm.box = "velocity42/xenial64"
    controller2.vm.network :private_network, ip: "192.168.2.4"
    controller2.vm.hostname = "controller2"
    controller2.vm.provision :shell, inline: 'cat /vagrant/client.pub >> /home/vagrant/.ssh/authorized_keys'
  end

  config.vm.define "worker0" do |worker0|    
    worker0.vm.box = "velocity42/xenial64"
    worker0.vm.network "private_network", ip: "192.168.2.5"
    worker0.vm.hostname = "worker0"
    worker0.vm.provision :shell, inline: 'cat /vagrant/client.pub >> /home/vagrant/.ssh/authorized_keys'
  end

  config.vm.define "worker1" do |worker1|
    worker1.vm.box = "velocity42/xenial64"
    worker1.vm.network :private_network, ip: "192.168.2.6"
    worker1.vm.hostname = "worker1"
    worker1.vm.provision :shell, inline: 'cat /vagrant/client.pub >> /home/vagrant/.ssh/authorized_keys'
  end

  config.vm.define "worker2" do |worker2|
    worker2.vm.box = "velocity42/xenial64"
    worker2.vm.network :private_network, ip: "192.168.2.7"
    worker2.vm.hostname = "worker2"
    worker2.vm.provision :shell, inline: 'cat /vagrant/client.pub >> /home/vagrant/.ssh/authorized_keys'
  end

  config.vm.define "load_balancer" do |load_balancer|
    load_balancer.vm.box = "velocity42/xenial64"
    load_balancer.vm.network :private_network, ip: "192.168.2.8"
    load_balancer.vm.hostname = "load-balancer"
    load_balancer.vm.provision :shell, inline: 'cat /vagrant/client.pub >> /home/vagrant/.ssh/authorized_keys'
  end

end
