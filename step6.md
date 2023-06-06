# STEP 6 - RETRIEVEING DATA FROM MYSQL DATABASE WITH PHP

## Connect to MySQL. Then run the following to command to create database
```
mysql> CREATE DATABASE `example_database`;
```
![create db](./images/Create%20database.png)

Create user and grant full privileges on the DB
```
mysql>  CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';
```

```
mysql> GRANT ALL ON example_database.* TO 'example_user'@'%';
```

Check database if created
```
mysql> SHOW DATABASES;
```
![show db](./images//show%20db.png)

## Create table
```
CREATE TABLE example_database.todo_list (item_id INT AUTO_INCREMENT, content VARCHAR(255), PRIMARY KEY(item_id);
```
Insert row of contest in the table
```
INSERT INTO example_database.todo_list (content) VALUES ("My first important item");
```
Then check table if row/s are inserted

![show table](./images/mysql%20table.png)

## Create a php file that will connect to MySQL

```
nano /var/www/projectLEMP/todo_list.php
```

Copy the following script
```
<?php
$user = "example_user";
$password = "password";
$database = "example_database";
$table = "todo_list";

try {
  $db = new PDO("mysql:host=localhost;dbname=$database", $user, $password);
  echo "<h2>TODO</h2><ol>";
  foreach($db->query("SELECT content FROM $table") as $row) {
    echo "<li>" . $row['content'] . "</li>";
  }
  echo "</ol>";
} catch (PDOException $e) {
    print "Error!: " . $e->getMessage() . "<br/>";
    die();
}
```

## Access the page in the web browser

Access it by going to the web browser and put your public IP with port 80 and appendeing /todo_list.php

![nginx host site](./images/PHP%20host%20site%20with%20DB.png)
