# STEP 4 — CONFIGURING NGINX TO USE PHP PROCESSOR

Create the root web directory for your_domain as follows:

```
sudo mkdir /var/www/projectLEMP
```
assign ownership
```
sudo chown -R $USER:$USER /var/www/projectLEMP
```
![new lemp directory](./images/lemp%20directory.png)

Open a new configuration file in Nginx's site-available directory

```
sudo nano /etc/nginx/sites-available/projectLEMP
```
Paste the following conifugiration
```
#/etc/nginx/sites-available/projectLEMP

server {
    listen 80;
    server_name projectLEMP www.projectLEMP;
    root /var/www/projectLEMP;

    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
     }

    location ~ /\.ht {
        deny all;
    }

}
```
![confiugration nginx](./images/configuration%20nginx.png)

Activate your configuration by linking the config file from Nginx' sites-enabled directory
```
sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/
```

Check syntax
```
sudo nginx -t
```
![syntax](./images/Nginx%20syntax.png)

Disable default Nginx host that is currently configured to listen to port 80

```
sudo unlink /etc/nginx/sites-enabled/default
```
After, reload Nginx to apply the changes
```
sudo systemctl reload nginx
```

## Create index file inside the project directory

```
sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP'
$(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html
```

Go to the browser and access the public address of your instance with port 80

![Nginx host](./images/Nginx%20site%20host.png)