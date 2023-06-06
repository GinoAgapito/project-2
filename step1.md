# STEP 1 - INSTALLING THE NGINX WEB SERVER
## Install Nginx server inside the Ubuntu instance
```
sudo apt update
sudo apt install nginx
```
verify that Nginx was successfully installed. It must be running and in green status
```
sudo systemctl status nginx
```
![Nginx running](./images/Nginx%20running.png)

Check the instance public address and go to browser to validate if Nginx is accessible

![Nginx browser](./images/Nginx%20browser.png)