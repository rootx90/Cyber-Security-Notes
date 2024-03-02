#WsCubeTech-CEH-notes 

---
### What we'll learn 
> Lecture Name : Enumeration
> 1) what is Enumeration
> 2) Types of Enumeration
> 3) Practical work - Types of Enumeration Scan
> 4) what next to do

---
### What is Enumeration
- after doing network scanning , the next step is Enumeration ✔
- define enumeration : 
	- means getting/extracting more extra information of that victim's System <br>(that we got after achieving those 5 Steps/Goals in network scanning) aka enumeration ✔<br>![[15_lecture-0-M3.jpg | 500]]
	- extra note by me : & finding the vulnerabilities by using those information to exploit the Victim's System aka exploitation 
- Ques : How Enumeration can be done ? Ans : by using "nmap" tool
- Ques : how we can do Enumeration by using "nmap" tool ? 
	- Ans : in "nmap" tool , it contains scripts - which are used sometimes for application (which are installed)
	- Ques : name the location where all applications installed files kept & sometimes those applications used when required <br>Ans : `usr/share` , in this location - we'll go `usr/share/nmap/scripts`
- Steps to find "scripts" folder of nmap <br>> STEP 1 : `sudo su` then `cd ../../` then `usr/share/nmap/scripts` <br>> STEP 2 : `ls`
	- Ques : what is a "script" mean ? <br>Ans : its a program which brings extra information from the victim's System <br>& these information are accurate & better which makes possible to hack the Victim's system <br>& mostly these script files brings information which makes possible to hack the system directly , not indirectly ✔ <br>- & some scripts are written only for one purpose i.e to bring information about the victim's system <br>- & scripts aka exe , means scripts are executable file ✔
	- Ques : in lecture 14 , we were doing network scanning to see open ports <br>then which was the 1st port no. & which service was running on that 1st port no. <br>Ans : port no. 21 & service running on it is FTP 
	- Ques : now find out how many scripts are inside `usr/share/nmap/scripts` whose name is FTP
		- Ans : so ![[15_lecture-1-M3.jpg | 500]]
		- we have many scripts of all the services are in networking , just like in pic - total 8 scripts of FTP service
		- Ques : what all these "scripts" of nmap tool does ✔? <br>Ans : if we run all these FTP scripts then these scripts will bring information only related to FTP service
		- Ques : these scripts are divided into parts , How ? <br>Ans : means on each port no. - a specific service is running like <br>> on port no. 21 - FTP service is running<br>> on port no. 22 - SMTP service is running<br>> on port no. 23 - Telnet service is running , etc. <br>- so each service is running on each port no. - we'll get scripts for each service
		- Ques : why we'll get scripts of each service which is running on each port no. <br>Ans : in "nmap" tool , these scripts bring advance/extra information about that Victim's system

### Types of Enumeration
- 2 types of Enumeration : Automation & manual
- Automation Enumeration
	- means let's say assume ✔<br>> 8 scripts of FTP service contain by "nmap" tool<br>> 6 scripts of HTTP service contain by "nmap" tool<br>> 5 scripts of SMTP service contain by "nmap" tool
	- now when we run "automation" enumeration scan then in "automation" enumeration scan <br>acc. to it's own requirement , it'll use that much scripts only of that service ✔ 
	- Eg : let's say we run scripts of FTP service , then acc. to "automation" enumeration scan , <br>it'll use either all 8 scripts of FTP service or no scripts of FTP service or 2 scripts , etc <br>but it all depends on "automation" enumeration scan - cuz it'll choose no. of scripts of scripts <br>acc. to it's own requirement ✔
	- command of "automation" enumeration scan or to run Automation script : `-sC` (small s & capital C) ✔
	- Advantage of it : it'll scan all the services of open ports step by step automatically ✔
	- Disadvantage of it : it'll take no. of scripts of services (of open ports) based on it's own requirement <br>means it can take either 1 or 2 or all or nothing or etc based on it's requirement ✔
- Manual Enumeration
	- command of "manual" enumeration scan or to run manual script : `--script` (small s & capital C) ✔
	- means it will scan only one service with all the scripts of that service at a time , not multiple at a time ✔
	- for Eg : <br>> 8 scripts of FTP service contain by "nmap" tool<br>> 6 scripts of HTTP service contain by "nmap" tool<br>> 5 scripts of SMTP service contain by "nmap" tool <br>- so here many scripts of each service , so "Manual" Enumeration will scan only <br>one of the service with all the scripts of that service 
	- Advantage : it'll scan all the scripts of that service which is scanning by it ✔
	- it used to get the advance information 
- Advantages of "Automation" & "Manual" Enumeration Scan
	- we used both of them one by one
	- firstly , we run "Automation" Enumeration then "Manual"
	- Ques : why we run "Automation" Enumeration first & then "Manual" ✔<br>Ans : cuz "Automation" Enumeration scan all the services <br>- so when it scan all the services then we'll get the idea of all the services <br>about of which service has more vulnerabilities or how much vulnerabilities have in each service <br>- so it'll bring a report about all the services <br>- Ques : so what we'll do - Ans : we'll get the idea i.e which service has more vulnerabilities <br>- let's say we got the idea that FPT service has more vulnerabilities
	- then we'll select the FTP service & we'll do "Manual" Enumeration Scan on FTP service 
	- so after doing "Automation" Enumeration scan , whatever information we'll get of FTP service <br>doesn't matter but we'll get the idea <br>> then we'll do "Manual" Enumeration scan & it'll scan all the scripts of that service (for eg : FTP service ) & <br>we'll get advance information about that service - let's say FTP service <br>> & that information contain advance details about that service (for eg : FTP service ) ✔

### Practical Work : Automation & Manual Enumeration Scans
- STEP 1 : firstly , we'll run "Automation" Enumeration Scan <br>`nmap -sS -v -p1-65535 192.168.224.128 -sC -sV -O -oX Saurabh.xml` & enter
	- Ques : to know how much percentage is done by "Automation" Enumeration Scan <br>Ans : either hit spacebar key or enter key of keyboard
- STEP 2 : now move that xml file `mv Saurabh.xml /home/kali` <br>Advice : don't save any file inside `usr/share/nmap/scripts` ✔
- STEP 3 : now going to this path `/home/kali` & do `ls`  to find that xml file
- STEP 4 : change that xml file into html file `xsltproc Saurabh.xml -o Saurabh.html`
- STEP 5 : exit from the root path `exit`
- STEP 6 : now open "Saurabh.html" file
	- STEP 6.1 : `/home/kali`
	- STEP 6.2 : `firefox Saurabh.html` - this file will get open in firefox browser
	- output pic : <br>![[15_lecture-2-M3.jpg | 500]]
	- so "Automation" Enumeration Scan run a script of FTP service i.e "FTP server status : to End of status" <br>- this is bandwith i.e from `No session .... to plain text` <br>- this is a version : "vsFTPd 2.3.4" 
	- & it's saying `Anonymous FTP login allowed (FTP code 230)` - means a vulnerability <br>means anonymous login is allowed - which tells that FTP service (running on that IP address) has vulnerability ✔
	- so "Automation" Enumeration Scan run only one script of FTP service i.e <br>![[15_lecture-3-M3.jpg | 500]]
	- & it try to scan & connect but due to this , only few information & version of FTP service we got <br>- & it also showed vulnerability i.e <br>![[15_lecture-4-M3.jpg | 500]]
	- it also shown that run the command on a SMTP script i.e "smtp-commands" <br>& if u run that command on SMTP then we can hack the system via SMTP service ✔<br>& that command is <br>![[15_lecture-5-M3.jpg | 500]]
	- Now Hope u got understood how to create the report of scanning 💡
- now we got to know that FTP service has a vulnerability i.e `Anonymous FTP login allowed (FTP code 230)` <br>so this is a big vulnerability , now we'll target & scan only FTP service via "Manual" Enumeration Scan ✔ 
- STEP 7 : now , we'll run "Manual" Enumeration Scan cuz we need advance information ✔
	- STEP 7.1 : `sudo su` & `nmap -sS -v -p21 192.168.224.128 --script=ftp* -sV -O -oX Saurabhmanual.xml
		- `--script=ftp*` : means <br>> `--script` : we're running "Manual" Enumeration Scan <br>> `ftp*` : means selecting particular service which we want to scan cuz <br>"Manual" Enumeration Scan can only scan only one service , so that's why - we define `ftp` <br>> `ftp*` : here star sign means anything written after `ftp` name <br>means scan all those files - which starts with `ftp` txt name ✔
		- `-p21` : means we define specific port no. i.e 21 <br>cuz "Manual" Enumeration Scan can only run on one port no. , <br>- multiple port no. can only be define in "Automation" Enumeration Scan <br>- so port no. of FTP service is `21` - that's why 21 defined ✔
		- Advice : u can remove the `-sV` means version - but keep the command complete for betterment
	- "Manual" Enumeration Scan will take time in order to give Advance information
	- STEP 7.2 : `ls` & then `xsltproc Saurabhmanual.xml -o Saurabhmanual.html`
	- STEP 7.3 : `exit` from root directory
	- STEP 7.4 : `firefox Saurabhmanual.html` - open in browser
	- output : we'll get advance information about each scripts of FTP service & advance information is <br>![[15_lecture-6-M3.jpg | 500]]
	- we'll learn about this Advance info - when we do exploitation in next lecture

### What next to do
- Ques : what does FTP service do ? <br>Ans : it used to transfer files <br>Ques : what does SMTP service do ? <br>Ans : used to send mails or do mailing <br>Ques : what does TELNET service do ? <br>Ans : used to make remote connection <br>- so due to these , we got to know that each protocol has their purpose of work ✔ <br>- so these are work of our protocols
- Ques : so if we hack that system via FTP service then - what access u'll get ? <br>Ans : i.e files <br>Ques : if we hack the system via SMTP <br>Ans : we'll get access of mail <br>Ques : if we hack the system via TELNET <br>Ans : remotely - we'll get access of that System ✔
- so in next lecture , we'll hack system via different protocols <br>- so first , we'll start with FTP protocol - we'll start making connection with FTP protocol <br>& whatever vulnerabilities we'll get - we'll use them to exploit that system - aka exploitation ✔ 
- there is a diff b/w services & protocols <br>- actually - all these services like FTP , SMTP , etc. - use TCP & UDP (which are protocols) ✔ <br>- but we say these services sometimes protocol too

---
### Homework
1. read about all different protocols for what each of them do & then in next lecture , we'll exploit <br>each protocol to make knowledge better <br>- protocols to know before coming to next lecture : <br>`ftp , ssh , telnet , smtp , DNS , http , rpcbind , netbios-ssn , exec , login , tcpwrapped , java-rmi` <br>- & note about what they do in doc file <br>- means make a PPT on all application Layer protocols

---
### End of the lecture (Doubts) :
1. Advice : when u were watching this lecture then "Manual" Enumeration Scan was taking time <br>so sir wait for sometime then he thought to understand next further topics
	- mine thought : wait for a while but don't for a thing for too long , do next thing which u have to do ✔


