# Tarea 4 - Reder en docker
> Realizado por Pablo R.

1. **Vamos a crear dos redes de tipo bridge con los siguientes datos:**
    - Red 1
        - Nombre: red1
        - Dirección de red: 172.28.0.0
        - Máscara de red: 255.255.0.0
        - Gateway: 172.28.0.1
    - Red 2
        - Nombre: red2
        - El resto de los datos serán proporcionados automáticamente por Docker.
        
        ```sh
            docker network create red1 --subnet 172.28.0.0/16 --gateway 172.28.0.1
            docker network create red2
        ```
        
        ![](./assets/ej1.PNG)
        
        Creamos las redes que se nos pide.
        
2. **Poner en ejecución un contenedor de la imagen ubuntu:20.04 que tenga como hostname host1, como IP 172.28.0.10 y que esté conectado a la red1. Lo llamaremos u1.**
        
    ```sh
    docker run -it --name u1 --network red1 --ip 172.28.0.10 ubuntu:20.04
    ```
    
    ![](./assets/ej2.PNG)
    
    Creamos el contenedor con la red1 y la ip proporconada en el ejercicio.
        
3. **Entrar en ese contenedor e instalar la aplicacion ping ( apt update && apt install inetutils-ping).**

    ```sh
        docker start u1
        docker exec -it u1 bash
        apt update
        apt install inetutils-ping
    ```
    
    ![](./assets/ej3.PNG)
    
    Iniciamos el contenedor, entramos por bash e instalamos la herramienta ping.
    
