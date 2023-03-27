## WEB STACK IMPLEMENTATION (LEMP STACK) project2

set up ec2 instance

connect ec2 to Terminal

'cd Downloads'

'ssh -i "mysecond-key.pem" ubuntu@ec2-34-230-43-36.compute-1.amazonaws.com'

'sudo apt update'

'sudo apt install nginx'

'sudo systemctl status nginx'

'curl http://localhost:80'

http://34.230.43.36:80

'curl -s http://34.230.43.36/latest/meta-data/public-ipv4'

'sudo apt install mysql-server'

'sudo mysql'

'ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';'

'mysql> exit'

'sudo mysql_secure_installation'

'sudo mysql -p'

'exit'

'sudo apt install php-fpm php-mysql'

'sudo mkdir /var/www/projectLEMP'

'sudo chown -R $USER:$USER /var/www/projectLEMP'

'sudo nano /etc/nginx/sites-available/projectLEMP'

'sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/'

'sudo unlink /etc/nginx/sites-enabled/default'

'sudo echo 'Hello LEMP from hostname' $(curl -s http://34.230.43.36/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://34.230.43.36/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html'

'sudo nano /var/www/projectLEMP/info.php'

'<?php
phpinfo();'

http://34.230.43.36/info.php#

'sudo rm /var/www/your_domain/info.php'

'sudo mysql'

'mysql> CREATE DATABASE `example_database`;'

'mysql>  CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';'

'mysql> GRANT ALL ON example_database.* TO 'example_user'@'%';'

'mysql> exit'

'mysql -u example_user -p'

'mysql> SHOW DATABASES;'

'CREATE TABLE example_database.todo_list (
mysql>     item_id INT AUTO_INCREMENT,
mysql>     content VARCHAR(255),
mysql>     PRIMARY KEY(item_id)
mysql> );'

'mysql> INSERT INTO example_database.todo_list (content) VALUES ("My first important item");'

'mysql>  SELECT * FROM example_database.todo_list;'

'mysql> exit'

'<?php
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
}'

'http://34.230.43.36/todo_list.php'



