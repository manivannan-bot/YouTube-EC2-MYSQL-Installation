# Commands used to host MySql Server on AWS EC2 Instance

## Step 1: Update the system

sudo apt update

## Step 2: Install MySql

sudo apt install mysql-server

## Step 3: Check the Status of MySql (Active or Inactive)

sudo systemctl status mysql

## Step 4: Login to MySql as a root

sudo mysql

## Step 5: Update the password for the MySql Server

ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'place-your-password-here';

FLUSH PRIVILEGES;

CREATE USER 'new_user'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO 'new_user'@'%' WITH GRANT OPTION;

FLUSH PRIVILEGES;
Instead, just go to /etc/mysql/mysql.conf.d/

There, you should find a file named mysqld.cnf

Here, you will find

bind-address = 127.0.0.1
Change it to

bind-address = 0.0.0.0 <OR> <Your IP>
THAT'S IT!!!. SAVE THE FILE AND RESTART MYSQL.


## Step 6: Test the MySql server if it is working by running sample sql queries

CREATE DATABASE mysql_test;

USE mysql_test;

CREATE TABLE table1 (id INT, name VARCHAR(45));

INSERT INTO table1 VALUES(1, 'Virat'), (2, 'Sachin'), (3, 'Dhoni'), (4, 'ABD');

SELECT * FROM table1;
