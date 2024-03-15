#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : Concept of DOS Attack
> 1) About : DOS attack
> 2) Types of DOS Attacks
> 3) Behind the scene : How DOS attack happens
> 4) Practical Work : DOS attack via hping3 tool 
> 5) Practical Work : buffer overflow attack
> 6) how to download jdk java v8

---
### About : DOS attack
- full form : denial-of-service
- Q : What it does
	- Ans : it makes the system's resources full
	- Q : what are resources mean in a system <br>Ans : Eg of System Resources : RAM , ROM , Processor , etc
	- so DOS Attack used to utilize all the resources of a system - in order to make that system slow/shut down
	- Primary goal of it : to slow or take down a website
- Eg : Q : what if i make ur processor to use or full 100% utilization - then what'll happen ✔
	- Ans : u'll say lag & at the end - system will not work properly
	- Q : what if i make ur RAM , storage full - then what will happen <br>Ans : when u start ur PC - then ur PC needs some storage to start the system <br>so if ur storage C:Drive gets full - then system will get crash
- Working of DOS (not the DOS attack)
	- a attacker wants to do DOS attacker to Victim's system via internet
	- Now let's say currently Victim's system capacity/limit is 10MB to process the packets at a time<br>- so attacker will generate & continuously send packets of 100MB , 200MB to Victim's system
	- Q : so what happen if Victim's system get 100MB , 200MB packets at a time <br>Ans : in Victim's system , Processor - not able to process stuff , RAM - couldn't able to load
	- so Victim's system can handle & process 10MB data at a time - but attacker sending 100MB data at a time <br>- so Victim's system will get crash eventually aka DOS Attack
	- Q : is this data virtual or real <br>Ans : real data sended
	- DOS attack doesn't happen on ROM , it only happens mostly on RAM & processor ✔ <br>- if a attack happens in ur ROM i.e HDD , SSD - aka Buffer Overflow attack ✔
- Conclusion Pic : <br>![[26_lecture-0-M3.jpg | 500]]

### Types of DOS Attacks
- 3 Types of DOS Attacks : <br>1) DOS attack <br>2) DDOS attack <br>3) DRDOS attack
- in DOS attack
	- Situation Eg : we have 2 systems i.e Attacker & Victim
	- at a time , Victim's system has a 10MB limit to handle & process the data packets <br>let's say Attacker's system has a 10MB limit to process & send the data at a time 
	- now Attacker wants to send a 5MB data packet
	- Q : can Attacker's system send total 10MB data packet a time to Victim's system <br>- Note : Attacker's system has a 10MB limit to send at a time <br>Ans : No , cuz Attacker's system also use it's own resources (like RAM , processor , storage , etc) <br>- & these resources will take storage to process & send the data packets <br>- so at a time , attacker's system can only process & send 5MB data packet to the Victim's system , <br>not the 100% 10MB data at once
	- when 5MB data packet go to the Victim's system - then Victim's system resources will be 50% utilized <br>- so once 50% resources (of Victim's system) will get full - then his/her system will lag <br>- cuz Victim's system still has 50% memory 
	- so aka DOS attack called <br>- when a attacker's system targeting & attacking to only one Victim's system : means 1 vs 1 fight ✔
	- Conclusion pic : <br>![[26_lecture-1-M3.jpg | 300]]
- in DDOS attack
	- Q : why we need DDOS attack ✔
		- Ans : in DOS Attack , <br>so here due to 10MB limit in attacker's system , <br>that's why - at a time , attacker's system able to send 5MB data packet - out of 10MB to Victim's system
		- if attacker wants to send 10MB data packets at a time - then attacker needs to do DDOS Attack ✔
	- full form : Distributed Denial of service
	- Working of DDOS Attack ✔
		- Attacker wants to crash a particular Victim's system <br>- so Attacker doesn't send the data packets directly to the Victim's system
		- firstly , Attacker will either hack or hire a group of multiple systems <br>- then Attacker will send the data packets or a command to those group of systems <br>& all those group of systems - will attack the Victim's system - to make slow/crash his/her system
		- let's say that group of systems contain 7 systems 
		- let's say Victim's system has a 10MB limit & can process only 10MB data at a time <br>- so let's say if attacker's system send the 2MB data packets - to each system's group <br>- & together those each system send the 2MB data packets - to Victim's system <br>- so Victim's system got total data i.e 14MB (7 systems * 2MB) - which is more than 10MB limit
		- even if those each system's group send 3MB - to Victim's system - then Victim's system will get crash for few hrs
		- so all a group of systems - will be run - acc. to the Attacker
		- so here data packets are distributed aka DDOS
	- Cons of DDOS attack ✔
		- this Cons is based on a situation & this situation will not be possible but let's see
		- Situation : <br>- what if Victim is a hacker - then he/she will hack any of the system (from that system's group) <br>- & this is obvious - that Attacker is giving a command to those each system <br>- then Victim (if he/she is a hacker) - will get the IP of the attacker's system - in those each system
		- then there's a chance of reverse-hacking will happen by Victim (if Victim is a hacker) to attacker 
	- Conclusion pic : <br>![[26_lecture-2-M3.jpg | 500]]
- in DRDOS attack
	- Q : why we need DRDOS attack ✔
		- Ans : in DDOS attack , <br>we saw a situation - where there's a change that the attacker's system can be hacked if Victim is a hacker
	- full form : Distributed Reflected DOS attack
	- Working of it
		- a attacker either hack or hire 2 group/layer of systems (many systems can be in each two groups) <br>- so attacker will give a command to 1st group of systems <br>- then that 1st group of systems - will give a command to 2nd group of systems - then the 2nd group of systems <br>will do DDOS attack to victim's system
		- so even if Victim (is a hacker) - then he/she couldn't able to hack other systems <br>- even he/she is able to hack any one of the system
		- so attacker hack or hire 2nd group of systems - in order to protect own main system's IP-address 
	- Conclusion Pic : <br>![[26_lecture-3-M3.jpg | 500]]
	
### Behind the scene : How DOS attack happens
- if we (as a attacker) send a data packet - then that data packet will go via any protocol - Eg : TCP
- let's take TCP protocol <br>Q : how TCP send data packets OR how TCP do communication b/w 2 devices<br>Ans : via TCP 3-way handshake
	- in TCP 3-way handshake <br>Q1) : from "System A" to "System B" , which packet/flag will go <br>Ans : SYN flag <br>Q2) in reply , SYN + ACK flag will come from "System B" to "System A" <br>Q3) "System A" send a ACK flag as a reply to "System B" 
- understanding a situation : Attacker vs Victim with TCP 3-way handshake
	- both attacker & Victim sitting on port no. 21 , <br>let's say attacker's system IP = 1.1.1.1 & victim's system IP = 4.4.4.4
	- so <br>1) Attacker send a data packet to Victim's system <br>2) then attacker got a reply from Victim <br>3) & then attacker send a reply to Victim <br>now connection established b/w Attacker & Victim
	- Q : is this complete TCP 3-way handshake will be considered as a DOS attack from attacker side ✔<br>Q : let's say Victim's system has a limit to process 1000 data packets at a time <br>& Attacker sent 10,000 data packets a time - is this called a DOS attack <br>Ans : data packets will go & come back to attacker & then again those packets will go to victim's system <br>- so this is not a DOS attack 
	- Q : why this is not a DOS attack <br>Ans : if u think that 10,000 sending & receiving will take time - but it's not , handshake will happen very quickly <br>- Eg : if sir send a Hi message via whatsapp - then do u feel that 3-way handshake happens ? Ans : No<br>- so TCP 3-way handshake happens very fast
	- here reply is coming properly from Attack to Victim - then from Victim to attacker <br>- so Firewall can block the IP <br>Q : what if attacker send those 10,000 data packets via different IP-addresses , still firewall block ✔ <br>Ans : No , cuz if attacker send half-half data packets via 2 different IP-addresses
	- understanding whether it's a DOS attack or not <br>1) attacker is sending 10,000 data packets to victim's system <br>2) then Victim's system will also get the reply of each data packets of 10,000 to attacker's system <br>- so here Attacker is getting it's own DOS attacke : means attacker doing reversed DOS i.e attacking himself ✔
	- so this is not a properly way of doing DOS attack <br>- so we don't want "SYN + ACK" reply getting from Victim's system to Attacker's system <br>- we only want to send "SYN" flag to Victim's system - for this - use a tool i.e "hping3" ✔
	- in hping3 tool , "--flood" option : which helps to block the reverse attack <br>i.e "SYN + ACK" reply from Victim's system will be blocked ✔

### Practical Work : DOS attack via hping3 tool
> Type of Attack : DOS Attack
> what we'll do : DOS attack meant to attack on processor + RAM
- STEP 1 : in metasploitable2 (i.e victim system) - check IP , run `ifconfig` , output : 192.168.186.138
- STEP 2 : in kali terminal , run `hping3 -help`
	- output : many options will be shown
		- syntax of hping3 : `hping3 host <options>`
		- useful options are 
			- in IP section , "-a , --spoof" : is a good option but it didn't used most of the time ✔
			- Q : what is spoof means ✔
				- Ans : let's a attacker's system IP is 10.2.20.20 <br>- & around his system's range - there's a someone's device - & IP of the device IP is 10.3.20.30 <br>- & there's a Victim's system IP = 10.2.20.10
				- & attacker wants to send the data packets via the device - whose IP is 10.2.20.30 - to Victim's system
				- so the DOS attack happens & data packets sent via <br>that someone's device to Victim's system , not via attacker's system ✔ <br>- this aka spoofing : means attacker did DOS attack by hiding his actual IP-address ✔ 
			- in UDP/TCP section , options are <br>> "-S , --syn" : it's more reliable ✔ <br>> "-p , --destport" : means destination port no.
			- in common section , options are : "-d , --data" <br>> "`-d , --data`" : used to specify the payload/data/file to be sent in the packet
			- "--flood" : sent packets as fast as possible - but it doesn't show/bring replies from the victim's system
	- STEP 2.0 : in metasploitable2 , run `top` : to open task manager , output : either 0.7 to 1% CPU is utilizing<br>- in kali , task manager showing 24% CPU is utilizing
	- let's see what happen to CPU in both (attacker's system as well as victim's system) - after executing DOS attack
	- STEP 2.1 : checking whether Victim's IP address are in our range of System's IP or not <br>- run `netdiscover`
	- STEP 2.2 : run `hping3 -S --flood -p 21 192.168.186.138`
		- in command - after "-p" , 21 port no. defined cuz 21 port no. used to establish the connection b/w 2 computers/Hosts ✔ <br>- Port no. 21 , 20 = used for FTP & port no. 20 : used to transfer data ✔
		- output : in victim's system , in task manager , 18.1% CPU get utilized
	- STEP 2.3 : open a new terminal , run same command from STEP 2.2 <br>- output : in victim's system - task manager - 14.3% - 20% (CPU utilizing will increase + decrease at the same time)
		- so "`hping3 -S --flood -p21 192.168.186.138`" : <br>- this command is attacking on (processor + RAM) of victim's system - aka DOS attack ✔
		- this command is sending data packets on port no. 21 <br>but Victim's system processor is getting utilize less - & processor of our (attacker) system is utilizing more ✔ <br>- so change port no. like 80 : means use a different port no. - where processor of victim's system <br>is utilizing more instead of in our system - then use that port no.✔
- one more command - which keep the processor in confusion state (means processor couldn't able to do processing) <br>& at the end processor will crash/corrupt ✔
- STEP 3 : in metaploitable2 system , run `cat /dev/urandom` : command will create random data
	- output : once u enter - then random values will be generated with a sound <br>- it'll happen for a while & then everything gets corrupted ✔
	- STEP 3.1 : press `CTRL + C` to stop it
	- STEP 3.2 : again run `cat /dev/urandom` without a sound , output : random data will be generated without a sound <br>- this command attacked on (Processor + RAM) of victim's system
	- STEP 3.3 : again press `CTRL + C` to stop <br>- output : everything gets corrupted & if u run `ls` - then nothing properly will come <br>![[26_lecture-4-M3.jpg | 500]]
	- in output , machine gets corrupted & if u run for more minutes - then this machine never going to be get fixed ✔
	- STEP 3.4 : to make the machine normal - restart it

### Practical Work : buffer overflow attack
- STEPS - doing buffer Overflow attack on victim's system directly
	- STEP 1 : in metasploitable2 , run `ls - l`
		- output <br>![[26_lecture-5-M3.jpg | 500]]
		- in output , "vulnerable" file size = 4096 (size could be in KB or MB)
	- STEP 2 : run `cat /dev/urandom >dos.txt` , hit enter & wait for a while 
		- output : we'll not get any output - cuz the command was saving everything in a file
		- STEP 2.1 : then press `CTRL + C`
		- STEP 2.2 : `ls -l` , output : <br>![[26_lecture-6-M3.jpg | 500]]
		- in output , see the size of dos.txt file & we just waited for 15sec <br>but if we wait a long - then "cat /dev/urandom >dos.txt" command will make the memory full in Victim's system ✔
		- aka Buffer overflow Attack
		- Note : running this same command on Kali OS - then kali OS will get corrupted
- STEPS - doing buffer Overflow attack via attacker's system
	- STEP 1 : in kali , run `sudo su`
	- STEP 2 : `gedit dos.sh` <br>- Note ✅ : to make a executable file in Kali , use `.sh` : means shell script , don't create txt file ✔
	- STEP 3 : write `cat /dev/urandom >dos.txt`
	- STEP 4 : run `chmod +x dos.sh`
	- STEP 5 : `ls -l` , output : 26 KB "dos.sh" file size
	- either u can run this file by urself via `./` command OR send to victim's system
	- STEP 6 : let's run in our kali , run `./dos.sh` - then press `CTRL + C`
	- STEP 7 : run `ls -l` , output : dos.txt file size = 396681216 in MB
	- for windows OS - a different way used 
	
### how to install jdk java v8
- Q : why we're installing java v8 <br>Ans : cuz might in future or when we're using "Ahmyth" too - then we need java v8 <br>& in Kali OS , only 2 different versions of java installed by-default 
- STEP 1 : search `open jdk java 8`
- STEP 2 : click on link of "openlogic" : [Site Unreachable](https://www.openlogic.com/openjdk-downloads)
- STEP 3 : select <br>1) Java version = 8 <br>2) OS = Linux <br>3) Architecture = x86 64-bit <br>4) java package = jdk
- STEP 4 : scroll down & download ".deb" file
- STEP 5 : `dpkg -i filename.deb` to install
- output : now 3 different version of java will come
- if u need jdk java 11 - then download from this website
- STEP 6 : to check how many java versions installed , run `udpate-alternatives --config java`

---
### Homework
1. check which port no. is utilizing more processor + RAM of the victim's system - instead of Attacker system

---
### End of the lecture (Doubts) :
- Q : when we do DOS attack & during DOS attack - data packets are generated , is those files saved in Victim's system ✔
	- Ans : Yes 
	- Q : how to check those saved files - in order to delete those files from Victim's system ✔<br>Ans : for delete - use `rm -r`
	- Q : is those files also saved when DOS attacked done on Victim's system Processor + RAM ✔<br>Ans : No , cuz no file created during executing the command for (Processor + RAM) <br>- but in Buffer Overflow attack , we saved the file  - cuz without saving a file - memory can't get overflow
	- Q : example - if someone doing DOS attack on my PC - & those files are not saved on my PC <br>then how i'll protect my PC ✔<br>Ans : DOS attack is never saved as a file in Victim's system - cuz it's not the attack which is saved as a file in Victim's system <br>- we can only stop that DOS attack - like firewall will protect from it <br>- but firewall is not configured/setup properly - then DOS attack can possible
- More about 
	- DOS Attack
		- [Denial of Service](https://home.ubalt.edu/abento/753/DoS/sld001.htm)
		- [Denial-of-Service(DoS) Attack. Series 2 Chapter 3 | by Anuja Pawar | Medium](https://medium.com/@anujapawar011/denial-of-service-dos-attack-3f8b726c1154) ✔
	- DRDOS attack : [About DrDoS Attack? — Definition by ThreatDotMedia](https://threat.media/definition/what-is-a-drdos-attack/)

