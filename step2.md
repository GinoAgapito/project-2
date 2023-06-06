# STEP 2 - INSTALLING MYSQL
Install MySQL by running the command in the server via terminal
```
sudo apt install mysql-server
```
When prompted, confirm installation by typing Y, and then ENTER.

When the installation is finished, log in to the MySQL console by typing:

```
sudo mysql
```
![SQL Installed](./images/MySQL%20Validation.png)

It’s recommended that you run a security script that comes pre-installed with MySQL
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';
```
This will ask if you want to configure the VALIDATE PASSWORD PLUGIN.

Note: Enabling this feature is something of a judgment call. If enabled, passwords which don’t match the specified criteria will
be rejected by MySQL with an error. It is safe to leave validation disabled, but you should always use strong, unique passwords 
for database credentials.

Answer Y for yes, or anything else to continue without enabling.


```
VALIDATE PASSWORD PLUGIN can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD plugin?

Press y|Y for Yes, any other key for No:
```


If you answer “yes”, you’ll be asked to select a level of password validation. Keep in mind that if you enter 2 for the strongest
level, you will receive errors when attempting to set any password which does not contain numbers, upper and lowercase letters, 
and special characters, or which is based on common dictionary words e.g PassWord.1.


```
There are three levels of password validation policy:

LOW    Length >= 8
MEDIUM Length >= 8, numeric, mixed case, and special characters
STRONG Length >= 8, numeric, mixed case, special characters and dictionary              file

Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG: 1
```


Regardless of whether you chose to set up the VALIDATE PASSWORD PLUGIN, your server will next ask you to select and confirm a
password for the MySQL root user. This is not to be confused with the system root. The database root user is an administrative user
with full privileges over the database system. Even though the default authentication method for the MySQL root user dispenses the
use of a password, even when one is set, you should define a strong password here as an additional safety measure. 
We’ll talk about this in a moment.


If you enabled password validation, you’ll be shown the password strength for the root password you just entered and your server
will ask if you want to continue with that password. If you are happy with your current password, enter Y for “yes” at the prompt:


```
Estimated strength of the password: 100 
Do you wish to continue with the password provided?(Press y|Y for Yes, any other key for No) : y
```


For the rest of the questions, press Y and hit the ENTER key at each prompt. This will prompt you to change the root password, 
remove some anonymous users and the test database, disable remote root logins, and load these new rules so that MySQL immediately
respects the changes you have made.

When you’re finished, test if you’re able to log in to the MySQL console by typing:


```
$ sudo mysql -p
```


Notice the -p flag in this command, which will prompt you for the password used after changing the root user password.

To exit the MySQL console, type:

```
mysql> exit
```

![SQL Installed](./images/SQL%20security.png)