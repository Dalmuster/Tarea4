# Instalación de Ubuntu, Apache, MariaDB, PHP y WordPress con Docker

## Ejercicio 1: Configurar un contenedor con Ubuntu y LAMP

### 1. Descargar la imagen de Ubuntu
```bash
sudo docker image pull ubuntu:22.04
```

### 2. Iniciar un contenedor con la imagen
```bash
docker run -it --name ubuntu22 -p 8000:80 ubuntu:22.04 /bin/bash
```

### 3. Instalar Apache
```bash
apt install -y apache2 apache2-utils
```

### 4. Instalar MariaDB
```bash
sudo apt install -y mariadb-server mariadb-client
```

### 5. Iniciar MariaDB
```bash
service mariadb start
```

### 6. Instalar PHP y configurarlo con MariaDB
```bash
mysql_secure_installation
apt install -y php php-mysql libapache2-mod-php
```

### 7. Instalar `systemctl` y reiniciar Apache
```bash
apt install systemctl
systemctl restart apache2
```

### 8. Crear el archivo `info.php`
```bash
echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/info.php
```

### 9. Acceder al contenedor desde el navegador
```
http://10.0.9.110:8000/info.php
```

![info.php](https://github.com/user-attachments/assets/6355a797-5c58-4857-8081-c8530a63dc2f)

---

## Ejercicio 2: Instalación y configuración de WordPress

### 1. Instalar paquetes necesarios
```bash
sudo apt install ghostscript libapache2-mod-php mysql-server php php-bcmath php-curl php-imagick php-intl php-json php-mbstring php-mysql php-xml php-zip
```

### 2. Descargar e instalar WordPress
#### Crear la carpeta para la instalación
```bash
mkdir -p /srv/www
chown www-data: /srv/www
```
#### Descargar y extraer WordPress
```bash
curl -o latest.tar.gz https://wordpress.org/latest.tar.gz
tar zx -C /srv/www -f latest.tar.gz
```

### 3. Configurar Apache para WordPress
#### Crear el archivo de configuración
```bash
touch /etc/apache2/sites-available/wordpress.conf
```
Debe quedar de la siguiente manera:
![apache-config](https://github.com/user-attachments/assets/920faa98-e62d-4a81-ae0a-68d534863a48)

#### Habilitar el sitio y módulos necesarios
```bash
service apache2 reload
a2enmod rewrite
a2dissite 000-default
service apache2 restart
```

### 4. Configurar la base de datos en MySQL
```bash
mysql -u root -p
```
![mysql-setup](https://github.com/user-attachments/assets/861a91c2-928a-4ea0-8c20-18cb27ebbc29)
![db-creation](https://github.com/user-attachments/assets/8532d0f9-c9a7-495d-a951-e730abbd5757)

### 5. Acceder a la instalación de WordPress
Abrir en el navegador:
```
http://tu-servidor/wordpress
```
![wordpress-install](https://github.com/user-attachments/assets/fd775915-9023-405e-b0df-a69d7bfd91f2)

### 6. Configurar `wp-config.php`
```bash
touch /srv/www/wordpress/wp-config.php
```
Configurar credenciales en `wp-config.php`:
![wp-config](https://github.com/user-attachments/assets/da47b4d1-0ddf-4b3d-b9cd-43449259df4c)

### 7. Verificar la instalación de WordPress
![wordpress-success](https://github.com/user-attachments/assets/c0d23af8-9d7f-4733-9a5b-2b3bdf73d0e0)

---

Este README documenta la instalación de un servidor LAMP en un contenedor Docker con Ubuntu 22.04, junto con la configuración de WordPress sobre Apache y MariaDB.

