# Linux Server Config Project


This project is the deployment of its companion project, proceding project [FSND-rchristy-project2](https://github.com/call900913/fsnd-rchristy-project2),
which is a web app that is essentially a list of items, otherwise known as an Item Catalog.

You can click [here](https://github.com/call900913/fsnd-rchristy-project2) to learn more about the web app.

The app is now live and living in a server.
At the time of this writing (about noon UTC-4, Aug 6 2019), you can visit the site by
opening your browser and typing this IP address on the address bar:
```
http://18.222.106.119
```

## The Project

The project itself was about taking a baseline installation of a Linux distribution (Ubuntu 16) provided by Amazon Lightsail.
It involves two servers: one to house the app, and the other one for the Database.

I secured the servers from a number of possible attacks and configured these machines to accomplish their respective missions.


### Summary of Softwares Installed

First, I updated ensured the softwares on the machine are up-to-date by running these commands on the Commnand Line:
```
$ sudo apt-get update

$ sudo apt-get upgrade

$ sudo apt-get autoremove
```

On the Web Server, the primary softwares installed are Apache HTTP Server, the WSGI module for Apache, the Flask framework for Python, and their dependencies;
on the Database Server, Postgresql.


### Summary of Configurations Made

After upgrading the softwares, I updated the `sshd_config` file to disable remote root login, disable remote password login, and determine ports for communication.

As per the rubric, I have added the user `grader` and given it `sudo` access and an RSA key for remote SSH login.

For security reasons, I have enabled `ufw` firewalls to close all ports for incoming connections except those required for the functioning of the app:
Port 2200/tcp (SSH), Port 123/udp (NTP), Port 80/tcp (HTTP) on the App Server and Port 5432/tcp on the Database Server.


### SSH Login

To SSH into the server, use this command:
```
ssh grader@18.222.106.119 -p 2200 -i ~/.ssh/priv_key
```


### Third-Party Resources Used

The following resources -- from the producers of softwares -- were consulted extensively in completing the project:
https://modwsgi.readthedocs.io/en/develop/index.html
https://www.postgresql.org/docs/9.5/index.html
https://github.com/call900913/fsnd-rchristy-project2
