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
