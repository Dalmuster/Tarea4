#Ejercicio 1

1-Descargar la imagen de ubuntu

--sudo docker image pull ubuntu:22.04

2-Iniciar contenedor con la imagen

--docker run -it --name ubuntu22 -p 8000:80 ubuntu:22.04 /bin/bash

3-Instalar apache

--apt install -y apache2 apache2-utils

4-Instalar Mariadb

--sudo apt install -y mariadb-server mariadb-client

5-Iniciar mariadb

--service mariadb start

6-Comandos para instalar php

--mysql_secure_installation

--apt install -y php php-mysql libapache2-mod-php

7-Instalar systemctl y reiniciar apache

--apt install systemctl

--systemctl restart apache2

8-Crear archivo info.php

--echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php

9-Acceder al contenedor desde el navegador

http://10.0.9.110:8000/info.php

![imagen](https://github.com/user-attachments/assets/6355a797-5c58-4857-8081-c8530a63dc2f)

#Ejercicio 2

1-Utilizar el comando para instalar los paquetes necesarios

--sudo apt install ghostscript libapache2-mod-php mysql-server php php-bcmath php-curl php-imagick php-intl php-json php-mbstring php-mysql php-xml php-zip

2-Crear la instalacion

--curl https://wordpress.org/latest.tar.gz | tar zx -C /srv/www


