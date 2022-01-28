# mallowz
Mallowz is an insecure webshop based on Apache, PHP and mySQL / mariaDB. 
It caused me physical pain to deliberately put the vulnerabilities in the code. 
But what the heck. The store can be used in security trainings, awareness demos, 
capture the flags and covers very many of the vulnerabilities discussed by OWASP.

<img src="./images/mallowz.png" width="50%">

In this repository, I'd like to explain the different approaches to building this store - starting with the system architecture. The store can be run on a ubuntu system with LAMP or a Windows system with xamp. Installation instructions for this can be found as well as tutorials for building a Docker environment in microservice architecture as well as a monolithic Docker approach.



## Installing mallowz on a Raspberry Pi with Ubuntu Linux
I did and described this already in a part of my Cloudberry Pi Cluster documentation. <br/>
If you are interedted in the Ubuntu installation on a Raspberry itself, please have a look here:
[Part 3: ubuntu install](https://github.com/jegali/Cloudberry-Cluster/blob/main/ubuntu-install.md)<br/>
Are you only interested in installing a LAMP (Linux, Apache, mySQL, PHP) environment on a Raspberry, please have a look here: [Part 7: LAMP](https://github.com/jegali/Cloudberry-Cluster/blob/main/install-lamp.md)<br/>



## The webshop as a microservice architecture
in 2020, I was able to participate in the Cloud native application architecture nano degree sponsored by Suse. An important part of this training was the use of microservices. And so, as an exercise, I built the webshop once as a microservice architecture. For the deployment there is a separate repository, the installation and configuration of the webshop I explain later. More information can be found here: [Project: Dockerized Webshop Environment](https://github.com/jegali/docker-nginx-mysql-php-phpmyadmin) 



## The webshop as a monolithic architecture
I would like to make the webshop available as a Docker image. In my microservice project, I deployed each service as a separate container, and mounted the directories with the database, source code and images as volumes. During the development of the webshop, this approach was invaluable - I could develop on my Windows machine and test directly in my containers. <br/><br/>
For sharing the store as a training tool, I think it is better to have a single container that has all the data, images and also the PHP source code on board. If the container is compromised during training, only a single container needs to be torn down and redeployed, no source code needs to be recopied, and no bugs need to be searched for. 
