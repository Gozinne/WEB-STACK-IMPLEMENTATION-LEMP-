# WEB-STACK-IMPLEMENTATION-LEMP-
</a>

![Contributors](https://img.shields.io/github/contributors/Gozinne/WEB-STACK-IMPLEMENTATION-LEMP-?style=plastic)
![Forks](https://img.shields.io/github/forks/Gozinne/WEB-STACK-IMPLEMENTATION-LEMP-)
![Stars](https://img.shields.io/github/stars/Gozinne/WEB-STACK-IMPLEMENTATION-LEMP-)
![Licence](https://img.shields.io/github/license/Gzinne/WEB-STACK-IMPLEMENTATION-LEMP-)
![Issues](https://img.shields.io/github/issues/Gozinne/WEB-STACK-IMPLEMENTATION-LEMP-)

## Setting up LEMP Stack on Ubuntu

### Lemp Stack Overview

You may come across terminologies like MEAN, MERN, LEMP, and LAMP when surfing the internet. 
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

***
<img
  src="https://user-images.githubusercontent.com/80969889/203666926-8e0ea8f1-174d-495e-9d6f-97559d85ec52.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
  
## Installing the NginX Web Server 
  
Nginx is the world's second most used web server, after Apache. Nginx supports all Unix-like and, to a lesser extent, Windows operating systems.

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

***
<img
  src="https://user-images.githubusercontent.com/80969889/204907347-1c79ae05-8e7f-4d40-bfc5-33fe184ddc36.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">
  
#Verify that nginx was successfully installed and running as a service in Ubuntu
```
sudo systemctl status nginx
```

***
<img
  src="https://user-images.githubusercontent.com/80969889/204907894-1364b955-d2f3-4795-9ee0-9a34f8683e75.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">

Our server is running and we can access it locally and from the Internet.
#Access it locally on Ubuntu shell
```
curl http://localhost:80
```

***
<img
  src="https://user-images.githubusercontent.com/80969889/204908430-3e7ff079-df70-418b-97bc-7e1b8f103130.png"
  alt="Alt text"
  title="Optional title"
  style="display: inline-block; margin: 0 auto; max-width: 300px">







































































