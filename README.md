# wordpress
## instalation in server
- ```sudo apt install apache2 php php-mysql libapache2-mod-php wget -y```
- ```sudo apt install mysql-client```
- ```wget https://wordpress.org/latest.tar.gz```
- ```tar -xzvf latest.tar.gz```
- ```sudo mv wordpress /var/www/html/```
- ```sudo cp /var/www/html/wordpress/wp-config-sample.php```
- ```/var/www/html/wordpress/wp-config.php```
- ```sudo nano /var/www/html/wordpress/wp-config.php```
---
## setting on database
```sql
( 'DB_NAME', 'wordpress_db' );
( 'DB_USER', 'your_rds_username' );
( 'DB_PASSWORD', 'your_rds_password' );
( 'DB_HOST', 'your_rds_endpoint' ); 
```
- ```sudo systemctl restart apache2```
---
