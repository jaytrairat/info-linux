# info-linux

## ubuntu clipboard
```bash
sudo apt update
sudo apt install build-essential dkms linux-headers-$(uname -r)
sudo apt install virtualbox-guest-x11
sudo VBoxClient --clipboard
```

## ubuntu composer
```bash
sudo apt install unzip php-cli curl
curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
HASH=`curl -sS https://composer.github.io/installer.sig`
php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
```

## nginx
```bash
sudo apt install nginx
sudo ufw allow "Nginx Full"
```

## mysql setup
```bash
sudo apt install mysql-server
sudo mysql
```

```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'SetRootPasswordHere';
exit
```

```bash
sudo mysql_secure_installation
```

## php setup
```bash
sudo apt install php-fpm php-mysql
```
