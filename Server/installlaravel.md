**Home**
- [Home](../index.md)
---

# Laravel Installation
## Install Prerequisites
- Install the software dependencies
  - `$ sudo apt install -y php-mbstring php-xml php-fpm php-zip php-common php-fpm php-cli unzip curl nginx`
- Install composer
  - `$ sudo curl -s https://getcomposer.org/installer | php`
  - `$ sudo mv composer.phar /usr/local/bin/composer`
- Github deploy key
  - Paste the text below, substituting in your GitHub email address
  - `$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`
  - Copy the generated `id_rsa.pub` and paste into Github
- Test ssh connection
  - `ssh -T git@github.com`
  - Following that click `yes`
- Mysql update user password plugin
  - To check users `select user,plugin,host from user;`
  - `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'mypassword';`

## To install a Laravel project from github use git clone followed by the folder name
- `git clone git@github.com:ZayRTun/glestate.git html`

## Webserver as owner (the way most people do it, and the Laravel doc's way)
- `sudo chown -R www-data:www-data /path/to/your/laravel/root/directory`

### you will have some problems uploading files or working with files via FTP, because your FTP client will be logged in as you, not your webserver, so add your user to the webserver user group
- `sudo usermod -a -G www-data ubuntu`

## Git errors
- `git reset --hard FETCH_HEAD`