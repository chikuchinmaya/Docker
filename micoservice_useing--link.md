# Microservice Architecture Using --link

1. **Start two CentOS containers c1 & c2 and create a link between them.**

    *Start CentOS container c1.*
    
    ```bash
    docker run --name c1 -it centos
    ```
    
    *Come out of c1 container without stopping it.*
    
    ```bash
    Ctrl+P & Ctrl+Q
    ```
    
    *Start another CentOS container c2 and link it with c1.*
    
    ```bash
    docker run --name c2 -it --link c1:aliasc1 centos
    ```
    
    *Check the link connection in c2 container.*
    
    ```bash
    ping c1
    ```
    
    *(It should ping if the link is established)*

2. **Start jenkins as container & name it as devserver, Start two tomcat container one for qaserver and another one for prodserver.On this enverment the jenkins admin should be perfom CI/CD.**

    *Start jenkins as container 
	
	```bash 
	docker run --name devserver -p 5050:8080 -d jenkins/jenkins
	```
	
	*Start tomcat server and link with devserver.*
	
	```bash 
	docker run --name qaserver -p 7070:8080 -d --link devserver:jenkins tomcat
	```
	
	*Start prodserver tomcat serverand link with devserver.*
	
	```bash 
	docker run --name prodserver -p 7071:8080 -d --link devserver:jenkins tomcat
	```	
	
	*Note: To access jenkins (devserver); prodserver; qaserver;*
	
	```bash
	http://public_ip:ports_numbe
	```
	
3. **create a LAMP Architecture where the O/S is Linux, database should be Mysql, the application server apache httpd and the programlanguale is PHP.**

    *Start Mysql as a container.*

	```bash
    docker run --name mydb -d -e MYSQL_ROOT_PASSWORD=chiku mysql
    ```
    *start httpd apache server and link with mysql container.*
	
	```bash
	docker run --name myweb -d -p 8081:80 --link mydb:mysql httpd
	```
	
	*Start a PHP server and link with my sql and httpd.
	
	```bash
	docker run --name php -d --link mydb:mysql --link myweb:httpd php:7.2-apache
	```
4. **create master slave form jenkins useing docker container.*
 
    *start jenkins as container.*
	
	```bash
	docker run --name master -d -p 8082:8080 jenkins/jenkins 
	```
	
	*start a ubuntu container and link the master server.*
	
	```bash
	docker run --name u1 -it --link master:jenkins ubuntu
	```
	
	*In ubuntu container download the slave jenkins/jenkins container.*
	
	```bash
	apt-get update
	```
	
	```bash 
	apt-get install -y wget
	```
	
	*Donload slave.jar file in ubuntu container.*
	
	```bash
	wget master:8080/jnlpJars/slave.jar
	```
	
5. **create a testing inverment where selenium hub container is linked with 2 nord containers.1 is for firefox & another with chrome install on it.

    *Start selenium hub as a container.*
	
	```bash
	docker run --name hub -d -p 4444:4444 selenium/hub
	```
	
	*Start chrome container and linked with selenium hub.*
	
	```bash
	docker run --name chrome -d -p 4444:4441 --link hub:selenium selenium/standalone-chrome
	```
	
	*Start firefox container and linked with selenium hub.*
	
	```bash 
	docker run --name firefox -d -p 4444:4442 --link hub:selenium selenium/standalone-firefox
	```
	
	*Note: The above containers we can see by useing VNC viwer.*
	
	a. Download & install VNC viwer on laptop.
	b. Open VNC viwer
	c. Type public IP of dockerhost:portnumber
	d. enter the password:- secrect
	
	===================================================
