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
        
        ![](./assets/ej1.png)
        
        Creamos las redes que se nos pide.
        
2. **Poner en ejecución un contenedor de la imagen ubuntu:20.04 que tenga como hostname host1, como IP 172.28.0.10 y que esté conectado a la red1. Lo llamaremos u1.**
        
    ```sh
        docker run -it --name u1 --network red1 --hostname host1 --ip 172.28.0.10 ubuntu:20.04
        docker start u1
    ```
    
    ![](./assets/ej2.png)
    
    Creamos el contenedor con la red1 y la ip proporconada en el ejercicio.
        
3. **Entrar en ese contenedor e instalar la aplicacion ping ( apt update && apt install inetutils-ping).**

    ```sh
        docker exec -it u1 bash
        apt update
        apt install inetutils-ping
    ```
    
    ![](./assets/ej3.png)
    
    Iniciamos el contenedor, entramos por bash e instalamos la herramienta ping.
    
4. **Poner en ejecución un contenedor de la imagen ubuntu:20.04 que tenga como hostname host2 y que esté conectado a la red2. En este caso será docker el que le de una IP correspondiente a esa red. Lo llamaremos u2.**

    ```sh
        docker run -it --name u2 --network red2 --hsotname host2 ubuntu:20.04
        docker start u2
    ```
    
    ![](assets/ej4.png)
    
    Ponemos en ejecución la segunda máquina.
    
5. **Entrar en ese contenedor e instalar la aplicación ping (apt update && apt install ineutils-ping)**.

    ```sh
        docker exec -it u2 bash
        apt update
        apt install inetutils-ping
    ```
    
    ![](assets/ej5.png)
    
    Instalamos la herramienta ping.
    
**PANTALLAZOS. Pantallazos.**

- Pantallazo donde se vea la configuración del contenedor u1.

```sh
    docker inspect u1
```

- Pantallazo donde se vea la configuración del contenedor u2.

![](assets/pantallazo1.png)

```sh
    docker inspect u2
```

![](assets/pantallazo2.png)

- Pantallazo donde desde cualquiera de los dos contenedores se peuda ver no hacemos ping al otro ni por ip ni por nombre.

```sh
    docker exec -it u1 bash
    ping u2
    ping 172.19.0.2
```

![](assets/pantallazo3.png)

Intentamos hacer ping desde u1 a u2.

- Pantallazo donde se pueda comprobar que si conectamos el contenedor u1 a la red2 (con docker network connect), desde el contenedor u1, tenemos al contenedor u2 mediante ping, tanto por nombre como por ip.

```sh
    docker network connect red2 u1
```

![](assets/pantallazo4.png)
