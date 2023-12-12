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
openssl genrsa -aes256 -out private-ca-key.pem 4096
openssl req -new -x509 -sha256 -days 365 -key private-ca-key.pem -out ca.pem
# openssl x509 -in ca.pem -text
# openssl x509 -in ca.pem -purpose -noout -text
openssl genrsa -out cert-key.pem 4096
openssl req -new -sha256 -subj "/CN=jaytrairat" -key cert-key.pem -out crt.csr
echo "subjectAltName=DNS:*jaytrairat.local,IP:192.168.9.10" >> extfile.cnf
openssl x509 -req -sha256 -days 365 -in cert.csr -CA ca.pem -CAkey ca-key.pem -out cert.pem -extfile extfile.cnf -CAcreateserial
cat cert.pem > fullchain.pem
cat ca.pem >> fullchain.pem
```
