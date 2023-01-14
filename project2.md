# PROJECT 2: LEMP STACK IMPLEMENTATION
## Step 1 – Installing the Nginx Web Server
### Install nginx
- `sudo apt update`
- `sudo apt install nginx`
- `sudo systemctl status nginx`
### Confirm that Nginx server can respond to requests from the Internet.
![NginX server](/images/nginx-server.jpg)

## STEP 2 — Installing mysql
### Install mysql
- `$ sudo apt install mysql-server`

![mysql install](/images/mysql-install.jpg)
### Log into mysql
- `$ sudo mysql`

![mysql login](/images/mysql-login.jpg)
### Set mysql root user password
- `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`
- `mysql> exit`
![mysql root user password](/images/rootuser-password.jpg)
### Log into mysql again after setting root user password
- `sudo mysql -p`
![mysql login](/images/rootuser-password.jpg)

## STEP 3 – Installingcd PHP
### Install PHP
- `sudo apt install php-fpm php-mysql`
![PHP install](/images/php-install.jpg)

## Step 4 — Configuring Nginx to Use PHP Processor
### Create root web directory domain
- `sudo mkdir /var/www/projectLEMP` 
### assign ownership
- `sudo chown -R $USER:$USER /var/www/projectLEMP`
### Open new configuration file in Nginx’s sites-available directory
- `sudo nano /etc/nginx/sites-available/projectLEMP`

![Blank file with bare-bones configuration](/images/blank-file-bareboneas-configuration.jpg)

### Activate configuration by linking to the config file from Nginx’s sites-enabled directory
- `sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/`

###  Test your configuration for syntax
- `sudo nginx -t`

![Test configuration for syntax error](/images/syntax-error-test.jpg)

### Disable default Nginx configured to listen on port 80
- `sudo unlink /etc/nginx/sites-enabled/default`
### Reload Nginx to apply the change
- `sudo systemctl reload nginx`
### Create an index.html file in the web root /var/www/projectLEMP directory
- `sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html`
![index.html](/images/html-index.jpg)
![web index.html](/images/web-html-index.jpg)

## Step 5 – Testing PHP with Nginx
### Creating a test PHP file in your document root. It is worthy of note that your php version must conform with the php version in your Nginx configuration.
- `sudo nano /var/www/projectLEMP/info.php`
![Tesst PHP file](/images/test--php-file.jpg)
![Tesst PHP with Nginx](/images/testing-php-with-nginx.jpg)

## Step 6 — Retrieving data from MySQL database with PHP
### First, connect to the MySQL console using the root account:
- `sudo mysql`
![Connect to database](/images/connect_database.jpg)
### Create a new database
- `mysql> CREATE DATABASE `example_database`;`
### create a new user and grant him full privileges
- `create a new user and grant him full privileges`
### give user permission over the example_database database:
- `GRANT ALL ON example_database.* TO 'example_user'@'%';`
### exit the MySQL shell
- `exit the MySQL shell`
![Create database & user](/images/create-database%26user.jpg)
###  Test if the new user has the proper permissions by logging in to the MySQL console again
-  `mysql -u example_user -p`
![database](/images/database.jpg)

### Create a test table named todo_list
- `mysql> INSERT INTO example_database.todo_list (content) VALUES ("My first important item");`
### Confirm that the data was successfully saved to your table
![Database](/images/confirm_-database.jpg)
![Retrieving data](/images/Retrieving-data-from-mysql-DB.jpg)



# SELF STUDY
[SQL syntax](https://www.w3schools.com/sql/sql_syntax.asp)

[Basic Nano commands](https://www.linuxandubuntu.com/home/nano-cli-text-editor-for-everyone-basic-tutorials)










