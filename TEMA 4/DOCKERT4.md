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
        
        