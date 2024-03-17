#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : Firewall Concept
> 1) Theory : what's firewall
> 2) Theory : types of firewall
> 3) Practical Work : prevent directory traversal vulnerability via firewall configuration

---
### Theory : what's firewall
- it has a rule book - which contains rules like <br>- which networks are safe to allowed in a client system for communication ,<br>- which network/IP-address is trying to enter forcefully in the client system , <br>- whenever u install any app in ur system - then firewall check whether that app taking away ur system's info (eg : rport , rhost) , <br>- it contains many more rules to make the system secure from outside network as well as internally
- it's a wall which monitor all the security stuff for that system

### Theory : Types of firewall
- 3 types of it <br>1) system/application firewall<br>2) Network firewall <br>3) Virtual firewall
- 2 forms of firewall <br>1) firewall could be in Hardware <br>2) or in software form <br>- but now a days , firewall is in software form
> Explanation : 3 Types of firewall
- System/application Firewall
	- in WinOS , is a inbuilt firewall in our system
	- Q : at ur home , many devices are connected to the router & even ur PC is connected with that router <br>- & Q : is will ur PC's firewall (which is installed in ur PC) protect the router or the other systems or only ur PC ✔️
		- Q pic : <br>![[36_lecture-0-M4.jpg | 500]]
		- Generally , each devices has it's own inbuilt firewall <br>but in this situation , assume those other systems don't have their own firewall - but ur PC has
		- Ans : ur PC only - cuz that firewall is of ur system
	- Q : now let's say a firewall is installed in that router <br>- so will that router's firewall protect all the systems (which are connected the router)
		- Ans : Yes - cuz when data comes - then it'll come 1stly via the Router's firewall
		- so that data will get filtered by router's firewall -> then it'll come to the router <br>-> then it'll come to those devices
		- & same as vice versa - means if any malicious activities going via any of those systems <br>then it'll go 1stly to the router -> then the firewall
	- Advantage of having a firewall in the router : all connected systems will get protected
- Virtual Firewall
	- it's like u installed Burp Suite & once u installed it <br>- then it'll give u an IP (let's say 127.0.0.1) & a port no. (assume 8080) <br>- then it'll say to u i.e put that (IP + port no.) in ur browser & whatever searched query u do <br>data/query go via BurpSuite
	- so Virtual firewall does
	- Eg : pfsense firewall - is an app
	- Q : what pfsense firewall does ✔️<br>Ans : it'll give an IP & a portno. - then we'll set that (IP + portno.) as proxy <br>due to this , data/searched-query will go via that (IP + portno.) <br>- same as data going via BurpSuite
	- for virtual Machine (Vmware) : pfsense firewall <br>for win OS : "windows defender firewall with Advanced Security"
	- firewall in winOS : there are 2 types of network i.e Inbound Rules & Outbound Rules <br>Inbound Rules : means coming from outside to inside <br>Outbound Rules : means going from inside to outside
	- Q : how to know whether that network (via which ur PC connected) is Public or Private ✔️<br>Ans : in WinOS , settings -> Network & internet -> Wifi -> open the wifi (via which ur PC connected)
	- acc to the type via which ur PC connected , rules will be made in "windows defender firewall with Advanced Security" <br>- so if u're connected with Public wifi - then "windows defender firewall with Advanced Security" will turn ON <br>those rules which are for Public <br>- same with private Wifi
	- in "windows defender firewall with Advanced Security" , we can make our custom new rules <br>STEP 1 : in "windows defender firewall with Advanced Security" -> click "Outbound Rules" <br>STEP 2 : on left panel -> click "New Rule" , output : options will shown on what basis u want to make a new rule <br>STEP 2 : select "Program" -> click "Next" btn , output : u want to make for "All Program" or "selected program" <br>STEP 3 : click "This Program Path" -> select Chrome browser -> click Next btn , output : options <br>STEP 4 : select "Allow the connection if it's secure" -> click Customize btn , output : we'll get many options <br>STEP 4.1 : select "Block the connection" -> click next btn , output : select profiles <br>STEP 5 : select only private option -> click Next btn <br>STEP 6 : name as "Test" -> click Finish btn <br>- output : in Outbound Rules , "test" rule will be created <br>- now if u change ur network profile from "Public Network" to "Private Network" like go to <br>settings -> Network & internet -> Wifi -> open the wifi (via which ur PC connected) <br>- then ur network gets closed & nobody can communicate <br>- Now delete that Rule - cuz it'll create issue means - when u switch into Private network - then chrome won't work <br>& u'll get worry
	- in kali OS 
		- generally , we don't need a firewall in Kali - cuz it's already secured
		- STEP 1 : `sudo su` -> `service apache2 start` -> `/var/www/html`
		- STEP 2 : `mkdir kasif` -> `cd kasif` -> `mkdir dev kapil saurabh sahil` <br>output : we made multiple folders in a folder
		- STEP 3 : in firefox's address bar , write "localhost:80" , output : apache page is online
		- STEP 4 : now write "localhost:80/kasif" , output : all those directories will be shown (which we created)
		- now let's open it on windows chrome browser
		- STEP 5 : check the IP of Kali & in windows OS - open chrome & write the IP:portno. <br>- like this `192.168.1.9:80` - output : apache page is online <br>STEP 5.1 : the write `192.168.1.9:80/kasif` , output : we can access those folders too <br>- advantage of it : u can share downloadable things locally from one system to another
		- in Window OS 
			- Q : in Win OS , who handle the port no. 80 ✔️<br>Ans : i.e IIS (Internet Information Services) - is a MS web server
			- Homework : search how to turn ON the localhost via IIS in window OS
		- Q : which vulnerability is it <br>Ans : directory traversal vulnerability <br>Q : why is it happen <br>Ans : it happens due to when firewall is not configured properly
		- Note : In kali OS , there's a inbuilt firewall - but it's by-default disable

### Practical Work : prevent directory traversal vulnerability via firewall configuration
- STEPS : to install firewall in Kali OS 
	- STEP 1 : `sudo su` -> `/home/kali`
	- STEP 2 : run `apt install libapache2-mod-security2`
	- Q : in kali OS , which folder contain all the installed applications setting files <br>Ans : "etc" folder
	- STEP 3 : `/etc` -> `cd modesecurity` , <br>output : "modesecurity.conf-recommended" need to edit the file name in order to make it work
	- Q : what's the command to edit the file name <br>Ans : mv 
	- STEP 4 : `mv modesecurity.conf-recommended modesecurity.conf` <br>- this command : means we'll change the file name - then move it - then keep it on same location <br>STEP 4.1 : `ls` - to check whether it gets renamed or not
	- STEP 5 : `gedit modsecurity.conf` -> remove the "#" from "SecRequestBodyAccess On" -> save the file
	- Q : in kali OS , by-default firewall aka <br>Ans : iptables
	- STEP 6 : run `iptables -h` , output : to check the options <br>- "modesecurity.conf" : is a setting file of iptables firewall
	- STEP 7 : `iptables -L` , output : <br>![[36_lecture-1-M4.jpg | 500]]
	- Q : the folder which we shared , will it come in INPUT or OUTPUT <br>Ans : i.e output
- we have a better firewall i.e "ufw" - cuz in "iptables" we need to ON or OFF all these 3 policies one by one manually <br>- but in "ufw" , we can turn ON or OFF in one go manually
- STEP 8 : run `ufw` , output : options will be shown of this firewall <br>STEP 8.1 : run `ufw enable` , output : many rules will be shown of this firewall <br>- but earlier "iptables" has only 3 policies <br>STEP 8.2 : run `iptables -L` , output : many rules will get applied
- STEP 9 : in firefox , run `localhost:80` , output : now that apache page will be shown <br>STEP 9.1 : run `localhost:80/kasif` , output : now that directory traversal vulnerability gets stopped <br>- it'll show "forbidden" <br>- means we can't switch the directory
- STEP 10 : now disable the "ufw" , run `ufw disable` -> then run in firefox `localhost:80/kasif` <br>- output : if still showing "forbidden" - then restart the apache service <br>STEP 10.1 : restart service apache , so run `service apache2 restart` <br>STEP 10.2 : in firefox , run `localhost:80/kasif` , output : we can access those directories <br>- earlier , it's not working by follow same steps - cuz previous firewall rules applied that's why

---
### Homework
1. 

---
### End of the lecture (Doubts) :
- Q : to download ParrotOS , which file format required for vmware <br>Ans : ISO for vmware
- Advice : in this lecture , sir trying different things again & again to resolve the issue & get the result <br>- so some stuff u won't remember always & some stuff u need to recall & some stuff u need to try ✔️
- in next lecture , main thing i.e clear logs - cuz is a part of system hacking 
- Advice : things to do once this course completed <br>1) learn more about nmap - cuz it itself is a course<br>2) Try do enumeration in all the services which we did with FTP <br>- like download win7 in vmware & do the numeration on it <br>3) learn & update urself

