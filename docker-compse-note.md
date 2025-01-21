***Docker Compose.***

**Install Docker Compose.**

* Go to Docker docs webisite and copy the CMD.*

```bash
https://docs.docker.com/desktop/setup/install/linux/
```

```bash
sudo yum update -y
```

```bash
sudo usermod -a -G docker ec2-user
```

```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

```bash
sudo chmod +x /usr/local/bin/docker-compose
```

```bash
docker-compose --version
```

1.  **Create a Docker Compose file for linking a mysql container with a wordpress container.*

* Create and edit file docker-compose.yml.

```bash 
vim docker-compose.yml
```

```bash

services:

  wordpress:
    image: wordpress
    restart: always
    ports:
      - 6060:80
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: chiku
      WORDPRESS_DB_PASSWORD: chiku
      WORDPRESS_DB_NAME: mydb
    

  db:
    image: mysql:8.0
    restart: always
    environment:
      MYSQL_DATABASE: mydb
      MYSQL_USER: chiku
      MYSQL_PASSWORD: chiku
      MY_SQL_ROOT_PASSWORD: chiku

```
	
-----------------------------------------------------------------
*To Create the architecture and running in the background.*
	
```bash
docker-compose up -d 
```
	
*To stop this architecture.*

```
docker-compose stop
```


	
