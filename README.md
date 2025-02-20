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

2-Creamos la instalación de wordpress

-Primero creamos la carpeta
mkdir -p /srv/www

-Le damos los permisos
chown www-data: /srv/www

-Descargamos el archivo
curl -o latest.tar.gz https://wordpress.org/latest.tar.gz

-Lo descomprimimos

tar zx -C /srv/www -f latest.tar.gz

3-Configuramos apache

touch /etc/apache2/sites-available/wordpress.conf

Debería quedar algo así

![image](https://github.com/user-attachments/assets/920faa98-e62d-4a81-ae0a-68d534863a48)

-Habilitamos el sitio

service apache2 reload

-Habilitamos la reescritura

a2enmod rewrite

-Desabilitamos el sitio predeterminado

a2dissite 000-default

-Reiniciamos apache

service apache2 restart

-Usando el commando vamos creando lo necesario

mysql -u root -p

![image](https://github.com/user-attachments/assets/861a91c2-928a-4ea0-8c20-18cb27ebbc29)

![image](https://github.com/user-attachments/assets/8532d0f9-c9a7-495d-a951-e730abbd5757)

![image](https://github.com/user-attachments/assets/8484b2dc-055a-4957-9e9b-1a7db814e023)

![image](https://github.com/user-attachments/assets/ad0f218c-01df-4ef8-9e60-0d7e420b7e27)

![image](https://github.com/user-attachments/assets/d4d4f461-5aa7-4413-b05c-bc34f66ee805)

5-Accedemos a wordpress

![image](https://github.com/user-attachments/assets/fd775915-9023-405e-b0df-a69d7bfd91f2)

6-Creamos el archivo de configuración

touch /srv/www/wordpress/wp-config.php

Esto es lo que debemos modificar

![image](https://github.com/user-attachments/assets/da47b4d1-0ddf-4b3d-b9cd-43449259df4c)


-Introducimos las credenciales

![image](https://github.com/user-attachments/assets/3dd0e713-9b8a-4318-9780-0c32d467cd2c)

-Verificamos que esta correctamente instalado

![image](https://github.com/user-attachments/assets/c0d23af8-9d7f-4733-9a5b-2b3bdf73d0e0)

