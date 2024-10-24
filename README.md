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

 --mv latest.tar.gz /srv/www

 --tar zxvf latest.tar.gz
