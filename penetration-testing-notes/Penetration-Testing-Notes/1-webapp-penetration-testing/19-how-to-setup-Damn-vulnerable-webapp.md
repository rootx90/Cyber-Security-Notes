#WAPT #penetration-testing
### Overview
- Lecture Name : How to setup Damn Vulnerable Web application (DVWA) in Ubuntu using Docker
### what we'll learn
- how to setup Damn Vulnerable Web App
- what is Docker & why it's useful for an application

---
### Topics - Explanation

1) <u>Steps - to setup Damn vulnerable Web App in Ubuntu</u>
	- we'll setup in Ubuntu & u can also setup it on kali Linux also but we want to setup in Ubuntu cuz to separate the attacker machine & victim machine
	- STEP 1: search `ubuntu ova` on google & click on `osboxes.org` url to download Ubuntu Virtual Machine
	- STEP 2: scroll down & download the `virtualBox` format of latest version of ubuntu 
	- STEP 3: download & install oracle VM (virtualBox manager)
	- STEP 4: in oracle VM, click file tab , select `import appliance` option & import that ubuntu virtual machine & run ubuntu & username + password both is `osboxes.org`
	- STEP 5: in Ubuntu , run commands
		- Note : in terminal , no commands will run cuz "osboxes@osboxes" won't give route permission , so run the command `sudo -i` & write the password i.e `osboxes.org` , now in terminal , we're on root directory
		- STEP 5.1: install docker `apt-get install docker.io` 
		- Define Docker : Docker is used to make the task easy so that application can be deploy , create , configure , etc becomes easier for developers . So it's a tool & inside of it , there are containers. Containers are like packages where all the important configurations are made in order to run an application like webservers , etc. So an application is published as a container on Docker ✔
		- STEP 5.2: `sudo systemctl enable docker` but we don't need `sudo` command cuz we're already in root directory , so run `systemctl enable docker`
		- so this command used to enable the docker & `systemctl` used to enable the services ✔
		- STEP 5.3: `sudo systemctl docker start` OR if u're already in root directory then run this `systemctl docker start`
		- STEP 5.4: run `docker run --rm -it -p 80:80 vulnerables/web-dvwa` 
		- this command used to run the container , so we're taking the container of dvwa & name of the container is `vulnerables/web-dvwa`
		- Why Docker is useful : cuz it makes the process easier otherwise to host an application take too much time cuz firstly "damn vulnerable application" needs to setup/configure in apache , etc.. configuration requires & we can follow the same steps to setup an application ✔
	- STEP 6: in firefox , write `localhost/setup.php` & dvwa webpage comes , so scroll down & click on `create / reset databases`
	- STEP 7: now login page will come , so it's a Damn Vulnerable WebApp , 
		- so username is `admin` & password is `password` & click `login` , output ![[WAPT-lecture-19-0.jpg]]
		- u can practice these attacks & u can setup dvwa security from "low" to "impossible" - according to that , dvwa configure itself
### Summary
1) `apt-get install docker.io`
2) `sudo systemctl enable docker` OR `systemctl enable docker`
3) `sudo systemctl docker start` OR `systemctl docker start`
4) `docker run --rm -it -p 80:80 vulnerables/web-dvwa`
5) open localhost/setup.php on browser
6) click on `create/reset databases`
7) login using username - `admin` & password - `password`
8) u can do any attackers which are on dvwa like `http://xyz/vulnerabilities/sqli/`


