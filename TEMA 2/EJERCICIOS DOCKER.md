# Tarea 2 - Imágenes - curso Docker - IESGN
> Realizado por Pablo R.

- **1. Descarga las siguientes imágenes: ubuntu:18.04, httpd, tomcat:9.0.39-jdk11,jenkins/jenkins:lts, php:7.4-apache.**

    ```sh
    docker pull ubuntu:18.04
    docker pull httpd
    docker pull tomcat:9.0.39-jdk11
    docker pull jenkins/jenkins:lts
    docker pull php:7.4-apache
    ```
    ![](assets/ejercicio1.PNG)
    ![](assets/ejercicio1-2.PNG)
    Descargamos las imagenes en el sistema.
   
    
-  **2. Muestra las imágenes que tienes descargadas.**
 
    ```sh
    docker images
    ```
    Comprobamos que estén correctamente descargadas.
    
    ![](assets/ejercicio1-3.PNG)
    
- **3. Crea un contenedor demonio con la imagen php:7.4-apache.**

    ```sh
    docker run -d -p 80:80 --name apache-php php:7.4-apache
    ```
    Creamos la imagen docker con php, y observamos que se visualiza correctamente en el navegador.
    
    ![](assets/ejercicio2-1.PNG)
    
    ![](assets/ejercicio2-2.PNG)
    
- **4. Comprueba el tamaño del contenedor en el disco duro.**
    ```sh
    docker ps -a -s
    ```
    Comprobamos que el tamaño del cotenedor es de 453MB siendo 2B virtuales.
    
    ![](assets/ejercicio4-1.PNG)
     
 - **5. Con la instrucción docker cp podemos copiar ficheros a o desde un contenedor. Puedes encontrar información es esta página. Crea un fichero en tu ordenador, con el siguiente contenido.**
    ```sh
    nano /home/daw/info.php
    ```
    ```php
    <?php
        echo phpinfo();
    ?>
    ```
    Creamos el fichero info.php con el código php en nuestra máquina host.
    
    ![](assets/ejercicio5-php.PNG)
    
    
    ```sh
    docker cp /home/daw/info.php apache-php:/var/www/html
    ```
    Copiamos el archivo info.php a /var/www/html de la maquina docker.
    
    ![](assets/ejercicio5-cp.PNG)
    
- **6. Vuelve a comprobar el espacio ocupado por el contenedor.**
    ```sh
    docker ps -a -s
    ```
    
    ![](assets/ejercicio6-ps.PNG)
    
    Observamos que el tamaño del contenedor ha pasado de 2B a 28B, después de transferir el archivo info.php.
    
- **7. Accede al fichero info.php desde un navegador web.**
    
    ![](assets/ejercicio7-web.PNG)
    
    Accedemos desde el navegador a la web y observamos que visualizamos correctamente el archivo php.
    
    http://172.17.0.2/info.php