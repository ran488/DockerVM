Vagrant.configure(2) do |config|
   config.vm.box = "ubuntu/trusty64"
   #set memory to 2GB...default is 489M
   config.vm.provider "virtualbox" do |v|
     v.memory = 2048
     v.cpus = 1
   end
   # the Vagrant docker provisioner doesn't do an update, so we have
   # to do it first
   config.vm.provision "shell", inline: "sudo apt-get update"
   # make sure to add proxy information before provisioning with docker, or else
   # docker won't know how to work
   config.vm.provision "shell",
		inline: "echo export http_proxy=${http_proxy} >> /etc/default/docker"
   config.vm.provision "docker"
   config.vm.provision :shell, :inline => "apt-get -qy install openjdk-7-jdk"
   #OpenJDK 8 doesn't work out of the box for Ubuntu 14.04, but we can still pull in Java 8 docker image
   #config.vm.provision :shell, :inline => "apt-get -qy install openjdk-8-jdk"
   config.vm.network "forwarded_port", guest: 8080, host: 8080
end
