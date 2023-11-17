# aws ec2 lamp
sudo dnf update -y
sudo dnf install -y httpd wget php-fpm php-mysqli php-json php php-devel
sudo dnf install mariadb105-server
sudo dnf info package_name
sudo systemctl start httpd
sudo systemctl enable httpd
sudo systemctl is-enabled httpd

to set file permission
sudo usermod -a -G apache ec2-user
exit
groups
sudo chown -R ec2-user:apache /var/www
sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \;
find /var/www -type f -exec sudo chmod 0664 {} \;

to test lamp 
echo "<?php phpinfo(); ?>" > /var/www/html/phpinfo.php
http://my.public.dns.amazonaws.com/phpinfo.php
sudo dnf list installed httpd mariadb-server php-mysqlnd
rm /var/www/html/phpinfo.php

To secure the MariaDB server
sudo systemctl start mariadb
sudo mysql_secure_installation

 Install phpMyAdmin
 sudo dnf install php-mbstring php-xml -y
 sudo systemctl restart httpd
 sudo systemctl restart php-fpm
 cd /var/www/html
 wget https://www.phpmyadmin.net/downloads/phpMyAdmin-latest-all-languages.tar.gz
 rm phpMyAdmin-latest-all-languages.tar.gz
 sudo systemctl start mariadb
 sudo systemctl start mariadb

 ip adress /phpinfo.php 
