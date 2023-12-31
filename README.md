# environment setup
## install vscode
```bash
sudo apt install apt-transport-https curl && curl -fsSL https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/microsoft.gpg > /dev/null && echo "deb [arch=amd64 signed-by=/etc/apt/trusted.gpg.d/microsoft.gpg] https://packages.microsoft.com/repos/vscode stable main" | sudo tee /etc/apt/sources.list.d/vscode.list && sudo apt update && sudo apt install code 
```

## install golang
```bash
sudo apt install golang
```

## install node
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash && . ~/.nvm/nvm.sh && nvm install node && nvm alias default node
```

## install docker
```bash
sudo apt install docker.io
```

## language
```bash
sudo dpkg-reconfigure keyboard-configuration
```

## docker mysql
```bash
docker run -dp 3306:3306 --name docker-mysql -e MYSQL_ROOT_PASSWORD=root -v /TEMP/mysql:/var/lib/mysql mysql:latest
```

## SSL

```bash
openssl genrsa -aes256 -out private.key 2048
openssl req -new -key private.key -out certificate.csr
openssl req -x509 -key private.key -in certificate.csr -out certificate.pem -days 36500
openssl x509 -in certificate.pem -text -noout
openssl rsa -in private.key -out private.pem

cat certificate.pem > certificate.crt
cat private.pem > certificate.crt


```
