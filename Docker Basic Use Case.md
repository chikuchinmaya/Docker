# Docker Use Case


1. Start Tomcat as a container in detached mode and map the Tomcat port 8080 with host port 5005.
# docker run --name webapp -p 5005:8080 -d tomcat

2. Start Jenkins as a container name it to "devserver" map port number 8080 with Jenkins port number 6060.
# docker run --name devserver -p 6060:8080 -d jenkins

3. Start ngnix as a container in detached mode and automatic port maping.
# docker run --name mywebpage -P -d ngnix
  Note: To identyfiy the port number # docker port mywebpage
  
4. Start a Ubuntu container and open ineractive teminal in it.
# docker run --name U1 -it ubuntu
 Note: To come out of container to host:- exit (It going to stop)
       With out stop the container and come out:- Ctrl+P & Ctrl+Q
	   
5. Start mysql is container and login and creact table.
# docker run --name mydb -d -e MY_SQL_ROOT_PASSWORD=password mysql
 Note: To open ineractive teminal in the host machine >>> #docker exec -it mydb bash
       To login into database >> mysql -u root -p >>>Enter the password
	   To see the list of tables >> show databases;
	   To move into a database >> use sys; >>>> Enter the database
	   To view the record of the tables>>>>> select * from <name>;
	   
	   
	   
