# wordpress
## instalation in server
- ```sudo apt update -y```
- ```sudo apt install apache2 php php-mysql mysql-client libapache2-mod-php wget -y```
- ```sudo systemctl start apache2```
- ```sudo systemctl enable apache2```
- ```wget https://wordpress.org/latest.tar.gz```
- ```tar -xzvf latest.tar.gz```
- ```sudo mv wordpress /var/www/html/```
- ```sudo cp /var/www/html/wordpress/wp-config-sample.php```
- ```cd /var/www/html/wordpress/wp-config.php```
- ```sudo nano /var/www/html/wordpress/wp-config.php```
-  ```sudo systemctl restart apache2```
---
## setting on database
```sql
( 'DB_NAME', 'wordpress_db' );
( 'DB_USER', 'your_rds_username' );
( 'DB_PASSWORD', 'your_rds_password' );
( 'DB_HOST', 'your_rds_endpoint' ); 
```
---
