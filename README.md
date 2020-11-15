Server & Environment Setup

---------------------------------
Install php 
---------------------------------
sudo apt install php7.4-common php7.4-mysql php7.4-xml php7.4-xmlrpc php7.4-curl php7.4-gd php7.4-imagick php7.4-cli php7.4-dev php7.4-imap php7.4-mbstring php7.4-opcache php7.4-soap php7.4-zip php7.4-intl -y

--------------------------------
Install NGINX
--------------------------------
sudo apt install nginx-full 
sudo service nginx status
sudo nano /etc/nginx/sites-available/phpmyadmin.conf
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
sudo apt-get install apache2
sudo nano /etc/apache2/apache2.conf 
sudo nano /etc/apache2/sites-available/000-default.conf

------------------------------------
Config MySQL
------------------------------------
sudo apt-get install mysql-server
mysql_secure_installation

--------------------------------
Install mariadb-server Mysql
-------------------------------
sudo apt install mariadb-server
sudo mysql_secure_installation
sudo systemctl status mariadb
sudo mysqladmin version

--------------------------------
Install phpmyadmin
------------------------------
sudo apt install phpmyadmin

--------------------------------
Project Setup
-------------------------------
1. git colne //
1. sudo apt-get install composer
2. composer install
3. cp .env.example .env
4. php artisan key:generate
5. nano .env
6. sudo a2enmod rewrite
7. sudo chmod -R 777 storage
7. sudo service apache2 restart
