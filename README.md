# WEB-STACK-IMPLEMENTATION-LEMP-
</a>

![Contributors](https://img.shields.io/github/contributors/Gozinne/WEB-STACK-IMPLEMENTATION-LEMP-?style=plastic)
![Forks](https://img.shields.io/github/forks/Gozinne/WEB-STACK-IMPLEMENTATION-LEMP-)
![Stars](https://img.shields.io/github/stars/Gozinne/WEB-STACK-IMPLEMENTATION-LEMP-)
![Licence](https://img.shields.io/github/license/Gzinne/WEB-STACK-IMPLEMENTATION-LEMP-)
![Issues](https://img.shields.io/github/issues/Gozinne/WEB-STACK-IMPLEMENTATION-LEMP-)

## Setting up LEMP Stack on Ubuntu

### Lemp Stack Overview

You may come across terminologies like MEAN, MERN, [LEMP](https://lempstack.com/), and LAMP when surfing the internet. 
These are web stacks, which are sets of tools, frameworks, and libraries used to create full-stack online applications. 
A database, server-side and client-side technologies, a web server, and a specific operating system are common components of a stack.
LEMP is an open-source web application stack for developing web applications. It's an acronym for 
* L = Linux Operating System.
* E - Nginx (pronounced engine-x, thus the E in the name), a web server.
* M = MySQL database.
* P = PHP is the programming language.
When a web browser requests a web page, the web server handles the request and passes it to server-side technologies such as a server-side scripting language like PHP to connect with the server and database.

### Requirements

The following items are required to begin and complete this project.
* An account logged into the AWS console.
* Open an AWS EC2 instance.
* Run the EC2 instance on Ubuntu and set the network security to: SSH,Port:22; HTTP,Port:80.
* Connect VScode or MobaXterm to the EC2 instance and launch a new terminal.

<img
  src="https://user-images.githubusercontent.com/80969889/203666926-8e0ea8f1-174d-495e-9d6f-97559d85ec52.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

## Installing the NginX Web Server 
  
[Nginx](https://nginx.org/en/) is the world's second most used web server, after Apache. Nginx supports all Unix-like and, to a lesser extent, Windows operating systems.

Why use Nginx?
* Installation and configuration are straightforward.
* Assist in load balance.
* Fastest for serving static files.
* It can handle more concurrent connections than Apache.
* Compatibility with popular programmes.


In this project Nginx will be used in order for website visitors to see the web pages.

#Update the server’s package index. 
```
sudo apt update
```
```
sudo apt install nginx
```


<img
  src="https://user-images.githubusercontent.com/80969889/204907347-1c79ae05-8e7f-4d40-bfc5-33fe184ddc36.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

#Verify that nginx was successfully installed and running as a service in Ubuntu
```
sudo systemctl status nginx
```


<img
  src="https://user-images.githubusercontent.com/80969889/204907894-1364b955-d2f3-4795-9ee0-9a34f8683e75.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

Our server is running and we can access it locally and from the Internet.

#Access it locally on Ubuntu shell
```
curl http://localhost:80
```

<img
  src="https://user-images.githubusercontent.com/80969889/204908430-3e7ff079-df70-418b-97bc-7e1b8f103130.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

It is time to check how Nginx server handles Internet queries.

#View the following URL in your preferred web browser
```
http://<Public-IP-Address>:80
```

<img
  src="https://user-images.githubusercontent.com/80969889/204909869-7cba92d5-c06a-4b4c-8fb3-739cd74383e3.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

## Installing MySQL

[MySQL](https://www.talend.com/resources/what-is-mysql/) is a [SQL-based open-source database](https://www.w3schools.com/sql/sql_intro.asp) that is used to store and process data while ensuring data consistency and integrity. It tabulates data by arranging it in rows and columns.  It is also ACID compliant.

Why use MySQL?
* It is completely free to use.
* Secure data storage.
* Extremely adaptive
* Outstanding performance.
* Scalability

#Again install this software
```
sudo apt install mysql-server
```  
To confirm installation, click **Y** and then **ENTER** when prompted.


<img
  src="https://user-images.githubusercontent.com/80969889/204912879-aafdf04b-0ffa-4db8-a30a-bc4316a2d6d4.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

#Enter this once installation is finished to launch the MySQL console
```
sudo mysql
```
 You should see output

<img
  src="https://user-images.githubusercontent.com/80969889/204913302-c218be92-37a4-48bd-8953-96af0b17747d.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

#To define the user's password as PassWord.1, enter
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';
```
Then exit the MySQL shell with: **exit**

#Start the interactive script by running
```
sudo mysql_secure_installation
```
A prompt will appear to configure the VALIDATE PASSWORD PLUGIN.
It is safe to leave validation disabled.
Therefore click on any key apart from **Y** to continue without enabling.

Regardless of whether the VALIDATE PASSWORD PLUGIN was activated, the server will prompt you to select and confirm a password for the MySQL root user. 
**<PassWord.1>** should be used. 
The server will display the password strength for the specified root password and prompt you to continue.

<img
  src="https://user-images.githubusercontent.com/80969889/204914021-ace89760-98c4-41d3-87e9-399c9e57b1d4.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

For the rest of the questions, press **Y** and hit the **ENTER** key at each prompt. 

<img
  src="https://user-images.githubusercontent.com/80969889/204916759-394a5efc-0267-46c7-a14a-76f303fe67ca.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

#Test the MySQL console by typing:
```
sudo mysql -p
```
Exit the MySQL console by typing **exit**.

<img
  src= "https://user-images.githubusercontent.com/80969889/204917220-92e9ce28-f0c1-4fd7-b42c-5853efd67bd4.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

 ## Installing PHP

[PHP](https://www.php.net/) stands for Hypertext Preprocessor and is a server-side programming language that interfaces with the database MySQL and performs all actions that the user asks such as obtaining data, adding data, altering data, and processing the data.

Why  use PHP?
* It is open-source and free.
* There is widespread community support.
* More database connectivity choices.
* Low-cost web hosting.
* WordPress, the most popular content management system, is written in PHP.

You've configured Nginx to serve content and MySQL to store and manage data. 
PHP must now be installed in order to read code and generate dynamic content for the web server.

#Install these 2 packages at once
```
sudo apt install php-fpm php-mysql
```
When prompted, type **Y** and press **ENTER** to confirm installation.

<img
  src= "https://user-images.githubusercontent.com/80969889/204918862-af365fae-6208-4f12-8c37-efab33415ff5.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

## Configuring Nginx to Use PHP Processor

We may establish server blocks (similar to virtual hosts in Apache) to encapsulate configuration data and host more than one domain on a single server when using the Nginx web server. 
**projectLEMP** is the domain name in this project. 

Nginx is set to serve content from the /var/www/html directory. 

#Create the root web directory for the domain.
```
sudo mkdir /var/www/projectLEMP
```
#Next, use the $USER environment variable to grant ownership of the directory to your current system user
```
sudo chown -R $USER:$USER /var/www/projectLEMP
```
#Using nano or vi command-line editor, create a new configuration file in Nginx's sites-available directory. 
```
sudo nano /etc/nginx/sites-available/projectLEMP
```

<img
  src="https://user-images.githubusercontent.com/80969889/204927565-b135ffcc-da2e-4ebe-ab6c-359ef11f8c11.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

#Copy and paste the following bare-bones configuration
```
#/etc/nginx/sites-available/projectLEMP

server {

 listen 80;

server_name: projectLEMP, www.projectLEMP;

 root /var/www/projectLEMP; 

 index.html, index.htm, index.php;


 location

     try_files $uri $uri/ = 404;

 }

 
 location .php$

     include snippets/fastcgi-php.conf;

     fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;

  }

 
 location /.ht

     deny all;

 }

 
}
```

<img
  src="https://user-images.githubusercontent.com/80969889/204927698-b65c03bf-4104-416d-9a69-c058540a3c90.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

Once you've finished editing, save and shut the file. 
For nano, press **CTRL+X**, followed by **y** and **ENTER**. 
For vi, use **Esc** to enter command mode, then type:**wq**. 

#Link to the config file from Nginx's sites-enabled directory to activate your configuration:
```
sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/
```
#Test configuration for syntax errors by typing
```
sudo nginx -t
```
The below message would be seen:

nginx: the configuration file /etc/nginx/nginx.conf syntax is ok

nginx: configuration file /etc/nginx/nginx.conf test is successful

#Disable the default Nginx host, which is presently set to listen on port 80

```
sudo unlink /etc/nginx/sites-enabled/default
```
#Reload Nginx when finished to implement the changes
```
sudo systemctl reload nginx
```
Although the new website is now operational, the web root /var/www/projectLEMP remains empty.

#Create an index.html file in that directory to verify that the new server block is functioning properly
```
sudo echo 'Hello LEMP from hostname' $(curl -s http://<Public-IP-Address>/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://<Public-IP-Address>/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html
```
#Open a browser and try to access your website
```
http://<Public-IP-Address>:80
```
<img
  src="https://user-images.githubusercontent.com/80969889/205390303-a32dda7e-7d74-438e-9017-a669f7744219.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

## Testing PHP with NginX

We build a test PHP file in your document root to ensure that Nginx can successfully pass PHP files to the PHP processor. 

#In a text editor, create a new file named info.php under the document root.
```
sudo nano /var/www/projectLEMP/info.php
```
#In the new file, type or paste this valid PHP code that will return information about your server.
```
<?php

phpinfo();
```
<img
  src="https://user-images.githubusercontent.com/80969889/205396949-4b4ad0c0-8fcf-4681-b99f-55d9ad502c73.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

#Now navigate to this website in your computer browser.
```
http://`server_domain_or_IP`/info.php
```
<img
  src="https://user-images.githubusercontent.com/80969889/205397030-834db9a7-6cc6-4310-93b0-52d6af0412e4.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

After reviewing the important information about the PHP server on that page, delete the file produced since it includes critical information about the PHP environment and the Ubuntu server.

#Delete that file using
```
sudo rm /var/www/your_domain/info.php
```
<img
  src="https://user-images.githubusercontent.com/80969889/205397182-6e463b12-b540-4552-b448-d4d2abb8606d.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

If you need it later, you can always regenerate it.

## Retrieving Data from MySQL Database with PHP

A database (DB) will be constructed with a simple "To do list" and access to it will be configured so that the Nginx website can query and show data from it.
Create a new user with the mysql native password authentication approach to connect to the MySQL database using PHP.
The database is called **example_database**, and the user is called **example_user**, but these names can be changed.

#To begin, log in to the MySQL console as the root user
```
sudo mysql
```
#Create a new database by running the following command from MySQL console
```
mysql> CREATE DATABASE `example_database`;
```
#The user's password is thus defined as password, although it may be updated with a safe password of choosing
```
mysql> CREATE USER 'example_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';
```
#Give this user permission over the example_database database
```
mysql> GRANT ALL ON example_database.* TO 'example_user'@'%';
```
#Exit the MySQL shell by typing **exit**, and then test by
```
mysql -u example_user -p
```
<img
  src="https://user-images.githubusercontent.com/80969889/205404292-c7329c34-883a-43e3-a974-435a79821ff6.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

#Confirm access to the example_database database
```
mysql> SHOW DATABASES;
```
This will give  the following output:

Output

+--------------------+

| Database        |

+--------------------+

| example_database   |

| information_schema |

+--------------------+

2 rows in set (0.000 sec)

***
Next, we’ll create a test table named todo_list.

#From the MySQL console, run the following statement:
```
CREATE TABLE example_database.todo_list (

mysql>  item_id INT AUTO_INCREMENT,

mysql>  content VARCHAR(255),

mysql>  PRIMARY KEY(item_id)

mysql> );
```
Insert a few rows of content in the test table. 

#Repeat the next command a few times, using different VALUES
```
mysql> INSERT INTO example_database.todo_list (content) VALUES ("My first important item");
```
#To confirm that the data IS successfully saved run:
```
mysql> SELECT * FROM example_database.todo_list;
```
You’ll see the following output:

Output

+---------+--------------------------+

| item_id | content               |

+---------+--------------------------+

|    1 | My first important item  |

|    2 | My second important item |

|    3 | My third important item  |

|    4 | and this one more thing  |

+---------+--------------------------+

4 rows in set (0.000 sec)

***
Then exit the MySQL console by typing **exit**.
<img
  src="https://user-images.githubusercontent.com/80969889/205404408-ffc55293-3985-44c2-b9a9-4e45c3d52b1b.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
***

#Now create a new PHP file in the custom web root directory using an editor
```
nano /var/www/projectLEMP/todo_list.php
```
#Copy this content into the todo_list.php script
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

Save and close the file when done.

In a web browser, navigate to this website by entering the domain name or public IP address.
```
http://<Public_domain_or_IP>/todo_list.php
```
You should see something like this, displaying the material you've entered into your test table.:

This indicates that your PHP environment is prepared to connect to and communicate with your MySQL server.
