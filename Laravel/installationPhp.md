**Home**
- [Home](../index.md)
---
# Installing php, mysql, apache, composer and laravel

**Before anything you should install git, curl, wget, … in a fresh ubuntu 18.04:**

```bash
sudo apt install -y git curl wget zip unzip
```
I put -y flag in the above command to answer all the question “yes” by default!

## Step 1 — Install Apache:

```bash
sudo apt install apache2
```

To make sure that the server is running check the apache2 status:

```bash
sudo systemctl status apache2
```
Then check this address in the browser : http://your_server_ip . In my case:
```bash
http://127.0.0.1
```

## Step 3— Install MySQL:

sudo apt install mysql-server

Optional:

Then remove some dangerous defaults after installing mysql:
```bash
sudo mysql_secure_installation
```
Think about a strong password for user root in Mysql ( in level 1=Medium, it must have sing, digit, lowercase and uppercase letters). Don’t forget to save it.
And then answer the other questions arise with Yes!

- Remove anonymous users? y
- Disallow root login remotely? y
- Remove test database and access to it? y
- Reload privilege tables now? y

Then you should try to connect mysql with root password
```bash
sudo mysql -u root -p
```
and when you see mysql> you can type exit to quit from mysql environment.  

## Step 4— Install PHP:
```bash
sudo apt install php libapache2-mod-php php-mysql
```
For Laravel installation and also phpmyadmin you will need some important php modules, so do this:

```bash
sudo apt install php7.2-common php7.2-cli php7.2-gd php7.2-mysql php7.2-curl php7.2-intl php7.2-mbstring php7.2-bcmath php7.2-imap php7.2-xml php7.2-zip
```
## Step 5— Add `phpinfo()`

```bash
sudo nano /var/www/html/info.php
```

And put this:
```php
<?php
phpinfo();
?>
```
Restart apache2
```bash
sudo systemctl restart apache2
```
Then check in the browser this: http://localhost/info.php

## Step 6— Install Composer
**Download Composer**

To quickly install Composer in the current directory, run the following script in your terminal.
```bash
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'e0012edf3e80b6978849f5eff0d4b4e4c79ff1609dd1e613307e16318854d24ae64f26d17af3ef0bf7cfb710ca74755a') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```
