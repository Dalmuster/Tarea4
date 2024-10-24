#Tarea 4

1-Consegir y entrarn en la imagen ubuntu 22.04 

--docker pull ubuntu 22.04

--sudo docker run ubuntu:22.04 /bin/sh

 #Ejercicio 1 
 1.Actualizar repositorio, instalar Apache 
 
 -apt update  
 
 --apt install -y apache2 apache utils  

 2.Instalar MariaDB  
 
 --apt install -y mariadb-server mariadb-client  
 
 --mysql_secure_installation

Se usa el commando para comprobar que esta ejecutandose

![imagen](https://github.com/user-attachments/assets/98c0713d-360e-4484-834e-8670a4a0b9ce)


 #Ejercicio 2

 1.Instalar dependencias

 --apt update

 --sudo apt install apache2 ghostscript libapache2-mod-php mysql-server php php-bcmath php-curl php-imagick php-intl      php-json php-mbstring php-mysql php-xml php-zip

2.Instalar wordpress

 --sudo mkdir -p /srv/www
 
 --sudo chown www-data: /srv/www

 --curl --output latest.tar.gz https://wordpress.org/latest.tar.gz

 --mv latest.tar.gz /srv/www

 --tar zxvf latest.tar.gz

3.Configurar apache para wordpress

 Crea el archivo wordpres.conf en el directorio /etc/apache2/sites-available/wordpress.conf

<VirtualHost *:80>
    DocumentRoot /srv/www/wordpress
    <Directory /srv/www/wordpress>
        Options FollowSymLinks
        AllowOverride Limit Options FileInfo
        DirectoryIndex index.php
        Require all granted
    </Directory>
    <Directory /srv/www/wordpress/wp-content>
        Options FollowSymLinks
        Require all granted
    </Directory>
</VirtualHost>

Recarga el servicio de apache2 una vez escrito el archivo

 --service apache2 reload

Activo el sitio

 --a2ensite wordpress

Habilita en modulo rewrite

 --sudo a2enmod rewrite

Desabilita la página por defecto

 --sudo a2dissite 000-default

 Por ultimo recarga la pagina

 --sudo service apache2 reload

 4.Crear base de datos

 Entro en el programa con el usuario root

  --mysql -u root

 Creo la base de datos wordpress , usuario, damos privilegios y los recargamos

  --CREATE DATABASE wordpress;

  --CREATE USER wordpress@localhost IDENTIFIED BY 'daniel';

  --GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,ALTER
    -> ON wordpress.*
    -> TO wordpress@localhost;
 
 --FLUSH PRIVILEGES;

5.Configurar wordpress para que se conecte a la base de datos

Copio el archivo de configuracion

  --cp /srv/www/wordpress/wp-config-sample.php /srv/www/wordpress/wp-config.php

Configuro el archivo de wordpress

sudo -u www-data sed -i 's/database_name_here/wordpress/' /srv/www/wordpress/wp-config.php
sudo -u www-data sed -i 's/username_here/wordpress/' /srv/www/wordpress/wp-config.php
sudo -u www-data sed -i 's/password_here/<daniel>/' /srv/www/wordpress/wp-config.php
  
