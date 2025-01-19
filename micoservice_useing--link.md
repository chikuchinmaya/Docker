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
