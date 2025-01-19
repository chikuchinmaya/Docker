# Docker Use Case

1. **Start Tomcat as a container in detached mode and map the Tomcat port 8080 with host port 5005.**

    ```bash
    docker run --name webapp -p 5005:8080 -d tomcat
    ```

2. **Start Jenkins as a container, name it "devserver", and map port number 8080 with Jenkins port number 6060.**

    ```bash
    docker run --name devserver -p 6060:8080 -d jenkins
    ```

3. **Start nginx as a container in detached mode with automatic port mapping.**

    ```bash
    docker run --name mywebpage -P -d nginx
    ```
    *Note: To identify the port number, use:*
    ```bash
    docker port mywebpage
    ```

4. **Start a Ubuntu container and open an interactive terminal in it.**

    ```bash
    docker run --name U1 -it ubuntu
    ```
    *Note: To exit the container to the host:*
    ```bash
    exit
    ```
    *(This will stop the container)*
    
    *To exit the container without stopping it:*
    ```bash
    Ctrl+P & Ctrl+Q
    ```

5. **Start MySQL in a container, log in, and create a table.**

    ```bash
    docker run --name mydb -d -e MYSQL_ROOT_PASSWORD=password mysql
    ```
    *Note: To open an interactive terminal in the host machine:*
    ```bash
    docker exec -it mydb bash
    ```
    *To log in to the database:*
    ```bash
    mysql -u root -p
    ```
    *Enter the password*

    *To see the list of databases:*
    ```sql
    show databases;
    ```
    
    *To move into a database:*
    ```sql
    use sys;
    ```
    
    *To view the records of the tables:*
    ```sql
    select * from <name>;
    ```
