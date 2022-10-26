# Tested in Debian 11 Server

## Firewall

```
sudo apt ufw install
```

![My Image](./images/image1.png)

```
sudo ufw enable
```

```
sudo ufw allow 22
```

## Nginx

```
sudo apt install nginx
```

![My Image](./images/image2.png)

```
sudo ufw allow 'Nginx Full'
```

```
sudo ufw allow 'Nginx HTTP'
```

```
sudo ufw allow 'Nginx HTTPS'
```

![My Image](./images/image3.png)

## MariaDB

```
sudo apt install mariadb-server mariadb-client
```

![My Image](./images/image4.png)

```
sudo mysql_secure_installation
```

![My Image](./images/image5.png)
![My Image](./images/image6.png)

```
sudo mysql
```

```
CREATE USER 'user'@'%' IDENTIFIED BY 'password';
```

```
GRANT ALL PRIVILEGES ON *.* TO 'user'@'%';
```

```
FLUSH PRIVILEGES;
```

```
EXIT
```

![My Image](./images/image7.png)

### Enable MariaDB Remote Access

```
sudo ufw allow 3306
```

![My Image](./images/image8.png)

```
sudo vim /etc/mysql/mariadb.conf.d/50-server.cnf
```

- Change this
  ![My Image](./images/image9.png)
- To this
  ![My Image](./images/image10.png)

- Restart MariaDB

```
sudo systemctl restart mariadb.service
```

## PHP

```
sudo apt install php php-mysql php-fpm
```

![My Image](./images/image11.png)

```
sudo vim /etc/nginx/sites-available/default
```

- Change this
  ![My Image](./images/image12.png)
- To this
  ![My Image](./images/image13.png)
- Change this
  ![My Image](./images/image14.png)
- To this
  ![My Image](./images/image15.png)

```
sudo systemctl restart nginx.service
```

## phpMyAdmin

```
sudo apt install phpmyadmin
```

![My Image](./images/image16.png)
![My Image](./images/image17.png)
![My Image](./images/image18.png)
![My Image](./images/image19.png)
![My Image](./images/image20.png)

```
sudo ln -s /usr/share/phpmyadmin/ /var/www/html/
```

![My Image](./images/image21.png)

# CodeIgniter 3 Problem

```
sudo vim /etc/nginx/sites-available/default
```

- Insert this

```
location /your-project {
    try_files $uri $uri/ /your-project/index.php;
}
```

![My Image](./images/image22.png)

```
sudo systemctl restart nginx.service
```
