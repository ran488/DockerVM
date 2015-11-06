Before doing any of this
- Install VirtualBox, Vagrant, SSH, CNTLM, (Ruby)
- make sure http(s)_proxy environment vars are set to get past corp proxy (using CNTLM).
- Vagrant proxyconf plugin installed and configured
 (HOME/.vagrant.d/Vagrantfile)
**
 Vagrant.configure("2") do |config|
   config.vm.box_download_insecure = true
   if Vagrant.has_plugin?("vagrant-proxyconf")
     config.proxy.http     = "http://10.0.2.2:3128"
     config.proxy.https    = "http://10.0.2.2:3128"
     config.proxy.no_proxy = "localhost,127.0.0.*,10.*,192.168.*,172.*,*.paychex.com,*.pxlabus.com"
   end
 end
**


To start VM....
% vagrant up

% vagrant ssh

Shared directory
> cd /vagrant

Port forward 8080, so you can access the running web app on your guest VM from your host machine's browser - http://localhost:8080

> git clone https://github.com/ran488/BootDockerGS.git
> vi gradle.properties (add proxy info)
> ./gradlew build buildDocker
> docker run -p 8080:8080 ran488/initial
