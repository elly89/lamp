## Initial Server Setup
1. Launch an EC2 instance with Ubuntu 22.04 LTS.
   - Hardware Requirements
   1. 4GB RAM
   2. 40GB Hard Disk
2. Connect to your instance via SSH
3. Update the system
```
sudo apt update && sudo apt upgrade -y
```
## Install Apache and Mysql
1. sudo apt install apache2 -y
 - Enable apache to start at boot
 ```
 sudo systemctl status apache2 && systemctl start apache2
 ```
2. sudo apt install mysql-server -y
 - secure mysql mysql installation
 ```
 sudo mysql_secure_installation
 ```
## Install PHP and to verify its intergaration with apache.
1. sudo apt install php libapache2-mod-php php-mysql -y
 - Restart apache to enable PHP and check version
 ```
 sudo systemctl restart apache2
 php -v
```
2. Test PHP Integration with Apache
 - sudo vi /var/www/html/info.php
  ```
  <?php
    phpinfo();
  ?>
  ```
## Test Database Connectivity
1. sudo nano /var/www/html/tphs.php
2. Add the following code to test the MySQL connection

 ```<?php
$servername = "localhost";
$username = "mmari";
$password = "123456";

// Create connection
$conn = new mysqli($servername, $username, $password);

// Check connection
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
echo "Connected successfully";
?>
```
3. Save the file and access it in your browser: Navigate to http://18.224.171.212/tphs.php/

# Database Setup and Operations

Database exercise  name is company_db

## Tables descriptions

###  Table 1 (Employees)

 1. This table store employees informations

+----------+--------------+------+-----+---------+----------------+
| Field    | Type         | Null | Key | Default | Extra          |
+----------+--------------+------+-----+---------+----------------+
| id       | int          | NO   | PRI | NULL    | auto_increment |
| name     | varchar(100) | YES  |     | NULL    |                |
| location | varchar(100) | YES  |     | NULL    |                |
+----------+--------------+------+-----+---------+----------------+

2. Create table statement for Table 1

```
CREATE TABLE `Employees` (
  `id` int NOT NULL AUTO_INCREMENT,
  `name` varchar(100) DEFAULT NULL,
  `position` varchar(100) DEFAULT NULL,
  `salary` decimal(10,2) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
```

### Table 2: Department

 1. This table store department informations

 +----------+---------------+------+-----+---------+----------------+
| Field    | Type          | Null | Key | Default | Extra          |
+----------+---------------+------+-----+---------+----------------+
| id       | int           | NO   | PRI | NULL    | auto_increment |
| name     | varchar(100)  | YES  |     | NULL    |                |
| position | varchar(100)  | YES  |     | NULL    |                |
| salary   | decimal(10,2) | YES  |     | NULL    |                |
+----------+---------------+------+-----+---------+----------------+

2. Create table statemnt for Table 2

```
CREATE TABLE `Departments` (
  `id` int NOT NULL AUTO_INCREMENT,
  `name` varchar(100) DEFAULT NULL,
  `location` varchar(100) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=3 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci |
```








    