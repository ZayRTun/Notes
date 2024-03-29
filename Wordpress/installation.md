**Home**
- [Home](../index.md)
---

# WordPress Installation

## Requirements
	- sudo apt-get install network-manager libnss3-tools jq xsel
	- sudo apt install php-cli php-curl php-mbstring php-xml php-zip
	- sudo apt install php-sqlite3 php-mysql php-pgsql
	- sudo apt install composer
	- sudo apt install curl

## Install mysql
	- sudo apt install mysql-server

	- sudo mysql
	- SELECT user,authentication_string,plugin,host FROM mysql.user;
	- ALTER USER 'root'@'localhost' IDENTIFIED WITH caching_sha2_password BY 'admin';
	- FLUSH PRIVILEGES;


## Install Valet
	- composer global require cpriego/valet-linux
	- valet install

## Set path if error - valet not found
	- echo "export PATH=$PATH:$HOME/.config/composer/vendor/bin" >> ~/.bashrc
	- source ~/.bashrc

## Configure Valet
	- mkdir ~/valet-sites
	- cd ~/valet-sites
	- valet park


## Install wp-cli
	- curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
	- chmod +x wp-cli.phar
	- sudo mv wp-cli.phar /usr/local/bin/wp


## Add wp-cli packages
	- wp package install git@github.com:aaemnnosttv/wp-cli-valet-command.git

## Reference Links -
	- Valet Linux: https://cpriego.github.io/valet-linux/index
	- Valet Linux Requirements: https://cpriego.github.io/valet-linux/requirements
	- WP-CLI valet commands: https://github.com/aaemnnosttv/wp-cli-valet-command#installing

## Video - How to setup localhost valet-linux and WordPress wp-cli commands on Ubuntu 20.04 LTS and other
	- https://www.youtube.com/watch?v=UFjtGOyErLk
