Server & Environment Setup

---------------------------------
Install php 
---------------------------------
1. sudo apt install php7.4-common php7.4-mysql php7.4-xml php7.4-xmlrpc php7.4-curl php7.4-gd php7.4-imagick php7.4-cli php7.4-dev php7.4-imap php7.4-mbstring php7.4-opcache php7.4-soap php7.4-zip php7.4-intl -y

--------------------------------
Install NGINX
--------------------------------
1. sudo apt install nginx-full 
2. sudo service nginx status
3. sudo nano /etc/nginx/sites-available/phpmyadmin.conf

server {
        listen 8080 default_server;
        listen [::]:8080 default_server;
        root /home/sayem/workspace;
        # Add index.php to the list if you are using PHP
        index index.php index.html index.htm index.nginx-debian.html;
        server_name _;
        location ~ \.php$ {
           include snippets/fastcgi-php.conf;
           fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
           fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
           include fastcgi_params;
            }
        }

--------------------------------
Install Apache2
--------------------------------
1. sudo apt-get install apache2
2. sudo nano /etc/apache2/apache2.conf 
3. sudo nano /etc/apache2/sites-available/000-default.conf

------------------------------------
Config MySQL
------------------------------------
1. sudo apt-get install mysql-server
2. mysql_secure_installation

--------------------------------
Install mariadb-server Mysql
-------------------------------
1. sudo apt install mariadb-server
2. sudo mysql_secure_installation
3. sudo systemctl status mariadb
4. sudo mysqladmin version

--------------------------------
Install phpmyadmin
------------------------------
1. sudo apt install phpmyadmin

--------------------------------
Project Setup
-------------------------------
1. git colne //
2. sudo apt-get install composer
3. composer install
4. cp .env.example .env
5. php artisan key:generate
6. nano .env
7. sudo a2enmod rewrite
8. sudo chmod -R 777 storage
9. sudo service apache2 restart

--------------------------------
Update Table Join
-------------------------------
1. ALTER TABLE categories CONVERT TO CHARACTER SET utf8;
2. ALTER TABLE category_translations  CONVERT TO CHARACTER SET utf8;
