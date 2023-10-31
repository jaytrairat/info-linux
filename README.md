# info-linux

# vm

## share clipboard between vm and host
```bash
sudo apt update && sudo apt install build-essential dkms linux-headers-$(uname -r) && sudo apt install virtualbox-guest-x11 && sudo VBoxClient --clipboard
```

## install docker
```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt install docker-ce docker-ce-cli containerd.io
sudo groupadd docker
sudo usermod -aG docker $USER
```

## install php
```bash
sudo apt install lsb-release ca-certificates apt-transport-https software-properties-common -y && sudo add-apt-repository ppa:ondrej/php && sudo apt install php8.2 -y
```

## install composer
```bash
sudo apt install unzip php-cli curl php-xml
curl -sS https://getcomposer.org/installer -o /tmp/composer-setup.php
HASH=`curl -sS https://composer.github.io/installer.sig`
php -r "if (hash_file('SHA384', '/tmp/composer-setup.php') === '$HASH') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
sudo php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer
composer install --ignore-platform-req=ext-curl
```

## ubuntu vscode
```bash
sudo apt install apt-transport-https curl
curl -fsSL https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/microsoft.gpg > /dev/null
echo "deb [arch=amd64 signed-by=/etc/apt/trusted.gpg.d/microsoft.gpg] https://packages.microsoft.com/repos/vscode stable main" | sudo tee /etc/apt/sources.list.d/vscode.list
sudo apt update
sudo apt install code
```

# native

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
