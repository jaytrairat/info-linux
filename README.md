# info-linux

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
