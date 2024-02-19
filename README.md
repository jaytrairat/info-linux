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

## run nginx for https with rev-proxy

### nginx.conf
```
server {
    listen 443 ssl;
    server_name 172.104.163.57;

    ssl_certificate /etc/nginx/certs/xxx.key;
    ssl_certificate_key /etc/nginx/certs/xxx.key;

    location / {
        proxy_pass http://172.104.163.57:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;

        # WebSocket support
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
    }
}
```

### run docker nginx
```bash
docker run -dp 443:443 --name nginx-docker -v ./xxx.pem:/etc/nginx/certs/xxx.pem -v ./nginx.conf:/etc/nginx/conf.d/default.conf nginx
```
