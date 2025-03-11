# WordPress Installation on EC2 Ubuntu Server

## 1. Update and Upgrade System
```bash
sudo apt update && sudo apt upgrade -y
```

## 2. Install Apache Web Server
```bash
sudo apt install apache2 -y
```
Check Apache status:
```bash
systemctl status apache2
```
Access Web Server:
```
http://<EC2_Public_IP>/
```

## 3. Install MySQL (MariaDB)
If not using RDS:
```bash
sudo apt install mariadb-server mariadb-client -y
```
If using RDS:
```bash
sudo apt install mariadb-client -y
```

## 4. Install PHP
```bash
sudo apt install php php-mysql -y
```
Test PHP installation:
```bash
sudo vim /var/www/html/info.php
```
Insert the following content:
```php
<?php
phpinfo();
?>
```
Access PHP test page:
```
http://<EC2_Public_IP>/info.php
```

## 5. Configure Database
### Local Database Configuration
```bash
sudo mysql -u root
```
Run the following SQL commands:
```sql
CREATE DATABASE wordpress_db;
CREATE USER 'wp_user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL ON wordpress_db.* TO 'wp_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

### RDS Database Configuration
Connect to RDS:
```bash
sudo mysql -h <RDS_Endpoint> -u admin -p
```
Run the following SQL commands:
```sql
CREATE DATABASE wordpress_db;
FLUSH PRIVILEGES;
EXIT;
```

## 6. Install WordPress
```bash
cd /tmp
sudo wget https://wordpress.org/latest.tar.gz
sudo tar -xvf latest.tar.gz
cd wordpress
sudo cp -R * /var/www/html/
```
Set proper permissions:
```bash
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/
sudo mkdir /var/www/html/wp-content/uploads
sudo chown -R www-data:www-data /var/www/html/wp-content/uploads/
```
Remove default files:
```bash
cd /var/www/html/
sudo rm -f index.html
```

## 7. Access WordPress
```
http://<EC2_Public_IP>/
```

## 8. WordPress Database Configuration
### Local Database
```
Database Name: wordpress_db
Username: wp_user
Password: password
Database Host: localhost
Table Prefix: wp_
```
### RDS Database
```
Database Name: wordpress_db
Username: admin
Password: <RDS_Password>
Database Host: <RDS_Endpoint>
Table Prefix: wp_
```

