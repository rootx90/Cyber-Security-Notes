#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : Session Hijacking
> 1) what is Session
> 2) what is Session Hijacking
> 3) Practical Work : Session Hijacking in a local system
> 4) what is MITM attack
> 5) Practical Work : Session Hijacking of a victim's system

---
### what is Session
- Define
	- when 2 different systems communication happen - then a session is created <br>- in order to maintain that communication b/w those 2 systems
	- means in order to establish a communication - a session is created - b/w 2 systems
- Eg : when we were doing testing in msfconsole - then we using vsftpd - then a message showing "vsftpd session 1 open"
	- when we hack + establish a connection 1st time - in victim's system = message will show "Session 1 is open" <br>- means we hacked the victim's system - via only one service i.e FTP
	- but let's say if we hack the Victim's system - via Telnet service - then message will show "Session 2 is open"
	- means the more we hack a system again & again via different service at a time - then that much new session no. will be created ✔ <br>- if same service used again & again to hack the system - then message will show "session 1" always ✔
	- Eg : in armitage , we're getting Shell 1 , Shell 2 , etc -> those are sessions
	- so when 2 systems get connected to each other - means a session is created b/w them <br>means connection b/w 2 systems = a session created b/w them ✔
	- Conclusion Pic of Example : <br>![[28_lecture-0-M3.jpg | 500]]

### what is Session Hijacking
- Q : what we do in Session Hijacking <br>Ans : in Session Hijacking , we'll Hijack the session - which is created b/w 2 computers - Eg : user & a facebook server
- Working of Session ✔
	- there's a F.B server & 4 users/persons are connected with the FB server <br>1st user) Eishan : login on FB & did a post <br>2nd user) Saurabh : liked on a post <br>3rd user) Kapil : commented on a post <br>4th user) ujjwal : he logout from his own account
	- so first-3 users will login inside their own FB account - then only they can do what they want <br>- so when "1st user" : login inside the FB server & did a post <br>- then "2nd user" : liked on a different post <br>- then "3rd user" : commented on a different post <br>- & "4th user" : was already logged in , so he logout from his FB account
	- Q : how server identified or got to know about :- <br>- these are the actual users who did something on FB via their own account<br>1) Eishan is a actual user : did a post <br>2) that "2nd user" : liked on a that post <br>3) that "3rd user" : did a comment on this post <br>4) that "4th user" : who logged out
		- currently , we took only 4 users , in world - there are many people who're using FB <br>- & at the same time , all are doing something on it
		- means Eg : when "4th user" logged out from his FB account - then why not logout happens with "1st user" FB account , <br>why FB account got logout happens with only "4th user" <br>- how server identify each users uniquely 
		- u'll say Database - but that's not complete answer
	- Ans : so whenever a connection establish b/w 2 systems
		- like when "1st user" : did login - so he put ID & password <br>- then login request packets goes to the FB server <br>Q : at 1st step - what that server did with the login request packet <br>Ans : firstly , that server will check - whether ID & password (of the user) is correct or not <br>Q : if ID & password is correct - then what request the server sent as a response <br>Ans : server gave a request (as a response) i.e the FB profile of the user + a sessionID ✔<br>- SID = sessionID <br>- so each client system will get only one unique sessionID from the server ✔
		- so the server will send a response to those 4 users with a unique sessionID to each user <br>let's assume each user got <br>1) "1st" user : got sID = 123 <br>2) "2nd user" : got sID = 456 <br>3) "3rd user" : sID = 789 <br>4) "4th user" : sID = 1122
		- so server gave a response + with a unique sessionID to each client <br>so if a user login in a FB & doing any activities - then packet will go with the sessionID to the server ✔
		- so in case with "1st user" <br>- when "1st user" login on FB - then login request goes to the FB server <br>- then server sent a response packet with a sessionID <br>Q : why a sessionID sent by the server to the user ✔<br>Ans : so that server can identify which client's request is this 
	- in WAPT journey 
		- in a response from the server, when the server send a sessionID = sessionID comes as aka setCookies (which is a header) <br>- that sessionID comes inside setCookies - setCookies send by the server ✔
		- in a request from client, sessionID goes via "cookies" header ✔
		- Conclusion : <br>- in a response packet from the server , sessionID comes via "setCookies" header <br>- in a request packet from the client , sessionID goes via "cookies" header 
	- so cookies = sessionID
	- Q : why sessionID goes via "cookies" header - inside the request packet from the client <br>Ans : cuz whatever activities u're doing like comment on the post <br>- at the end - then that comment packet - will save inside the server (of that app) <br>- so whatever activities u do in the app - that sessionID will go via "cookies" Header - to the server
	- so the request is going with sessionID to the server <br>Q : what if we hijack the sessionID of the client
	- Q : when will user get the sessionID from the server <br>Ans : when the user did completely all the process - then the server will authenticate the user in the app <br>- then only that user will get the sessionID
	- Q : should i hack username + password OR sessionID of the client - which one is better with a reason✔<br>Ans : hacking username + password - then might be user kept 2FA - then he/she will get OTP in phone <br>- but hacking the sessionID - is might better - cuz when user login - then the server will sent a response with a sessionID <br>as earlier said - sessionID got the user only when the user completely authenticate <br>- so by-default we (as a attacker) getting sessionID with authenticate in app <br>- so when we need to paste the sessionID - then directly login in the app/webapp (in the victim's account)
- Conclusion Pic ✔ : <br>![[28_lecture-1-M3.jpg | 500]]

### Practical Work : Session Hijacking in a local system
- Advice : we'll use that website which we have the permission to do hacking practice
- Practical Work : Session Hijacking in local system
- STEP 1 : locally either search "vulnhub.php" OR [Home of Acunetix Art](http://testphp.vulnweb.com/)
	- Q : where sessionID exists if a person didn't login in a website
	- Ans : go this website : [Home of Acunetix Art](http://testphp.vulnweb.com/) <br>1) inspect -> storage tab -> Cookies Header -> click on website URL , <br>- output : there's nothing cuz 
	- let's login
	- STEP 1.1 : click on Signup -> put default "test" as UN & pass , <br>- output : once u login in - then we'll get a sessionID <br>![[28_lecture-2-M3.jpg | 500]]
	- in output : <br>- in Name Column = login <br>- in value column = test%2Ftest - it's a sessionID ✔
- STEP 2 : copy the sesssionID
- STEP 3 : logout from the website & reload the website
- STEP 4 : in firefox , inspect -> storage tab -> cookies header -> click on website , output : no cookies is there
- STEP 5 : in website -> click "Logout test" btn , then reload the website
- STEP 6 : in Cookies header -> click on website link -> on right side , click "+" btn <br>1) in Name column - write "login"<br>2) in value column , paste that sessionID "test%2Ftest"<br>- hit enter
- STEP 7 : in website , click "your profile" , output : automatically login
- so via sessionID , u can login automatically in that website (without un & password) <br>- by putting the sessionID of that website

### what is MITM attack
- before doing Session Hijacking of a Victim's system , first need to understand MITM
- full form : (Man in the middle) attack
- Explanation ✔
	- there are 2 systems which are communicating each other
	- Q : how those 2 systems gonna communicate each other ✔<br>Q : who's the intermediator b/w them <br>Q : who's the centralize system - via which those 2 systems are talking each other <br>- server : is not a answer <br>Q : at home , what u use to do surfing in the internet <br>Ans : answers of all ques = router
		- Eg : a victim's system did a search -> & that packets goes to the router -> then that packets goes to the server <br>- so router = is a middle system b/w those 2 systems ✔
	- whatever communication going on b/w 2 systems , we (as a attacker) sit b/w those 2 systems <br>& capture the data packets (request + response) of those 2 systems ✔
	- this process aka MITM <br>- cuz a attacker comes b/w 2 systems & capture the data packets of those 2 systems
	- Q : can MITM possible on Victim's phone SIM <br>Ans : Yes <br>- SIM actually works like router - so it has one Public IP & one Private IP <br>- so in phone's setting - u search IP & the IP shown = Private IP <br>& when u go on browser to search IP on website like whatsmyip = Public IP
	- Conclusion Pic <br>![[28_lecture-3-M3.jpg | 350]]

### Practical Work : Session Hijacking of a Victim's system
- Q : when Session Hijacking performed ✔<br>Ans : when someone is near to ur network range <br>Q : if we want to take the sessionID of victim's system - then How to take it - we'll see in further STEPS
- Requirement : in VMware , must have 2 OS : Kali OS & Parrot OS
- STEPS : Practical Work : Session Hijacking of a victim's system
	- Parrot OS - Victim's system & Kali OS - attacker system
	- STEP 0 : ON both OS -> `sudo su`
	- STEP 1 : in Victim's system <br>> STEP 1.1 : in Parrot OS -> in firefox -> open http://testphp.vulnweb.com/
	- we (as a attacker) - use 2 tools : ettercap-graphical & wireshark ✔<br>- ettercap-graphical : used to capture data packets from the middle via MITM attack <br>- wireshark : 
	- STEP 2 : in attacker's system
		- STEP 2.1 Kali OS -> open Ethercap
		- output : <br>![[28_lecture-4-M3.jpg | 500]]
		- in output , eth0 : means right now our internet is connect with wire ✔<br>- if u're connected with wifi - then use WLAN0
		- STEP 2.2 : in Ettercap -> click on check-Box -> click "Hosts List" icon , output : <br>![[28_lecture-5-M3.jpg | 500]]
		- in Pic , more Hosts are not showing - so we'll do a search
		- STEP 2.3 : click on "search" icon , output : all the Host Lists will be shown - around our IP's range <br>![[28_lecture-6-M3.jpg | 500]]
		- in output pic , 192.168.186.142 : is a IP of Victim's system (parrot OS)
		- STEP 2.4 : Q : as a target 1 - which system do u want to listen the communication/data-packets
			- Ans : Parrot OS
			- STEP 2.4.1 : in Ethercap -> select Parrot OS IP -> click "Add to Target 1" , output : IP of Victim's system selected as target-1 <br>![[28_lecture-7-M3.jpg | 500]]
			- Q : acc. to u which IP is Target 2 <br>Ans : 1st one i.e 192.168.186.1 - is our system's router's IP <br>- cuz data packets goes from attacker's system to attacker system's router - then Victim's system
		- STEP 2.5 : select 1st IP -> click "Add to Target 2" -> click on "world shape" btn (which is a MITM menu)
			- "hexagonal shape" btn : used to stop & start the MITM attack
			- sniff : means keeping an eye on something or spying
			- STEP 2.5.1 : select "ARP poisoning" -> tick only "sniff remote connections" -> click OK  , output <br>![[28_lecture-8-M3.jpg | 500]]
			- STEP 2.5.2 : hover on "hexagonal shape" btn - if "Stop MITM" - means MITM is started <br>![[28_lecture-9-M3.jpg | 500]]
		- Now Ettercap tool : is listening via MITM , it'll not show data packets <br>- means it selected both the target & listening - but it won't show data packets ✔ <br>- in order to see data packets , use wireshark tool ✔
		- STEP 2.6 : in Kali -> open wireshark tool , 
			- output : <br>![[28_lecture-10-M3.jpg | 500]]
			- in output , in wireshark tool - those are different network <br>- so we'll select "eth0" network
		- STEP 2.7 : in wireshark tool , double click on "eth0" network , output : <br>![[28_lecture-11-M3.jpg | 500]]
		- now mostly for main tasks we'll use wireshakr tool <br>& Ethercap tool - maintain the connection b/w 2 systems (i.e attacker system's router + Victim's system) ✔
	- STEP 3 : in Victim's system
		- STEP 3.1 : login inside that website , output : once u logged-In inside the website - keep it as it is
	- STEP 4 : in Attacker's system
		- STEP 4.1 : in wireshark tool , click "search" icon -> click "Display Filter" dropdown-menu -> select String <br>- "String" : is also a display filter - which we need
		- STEP 4.2 : click "Packet List" dropdown-menu -> select "Packet bytes"
		- output of STEP 4.1 & 4.2 : we selected filter i.e we need values in (String + Packets in Bytes)
		- Q : acc. to u - which thing we need to search - in order to get data packets of Victim's system ✔<br>Ans : if u say session id - then it's wrong answer <br>- there u defined login & password , so we need either login or password
		- STEP 4.3 : in "find" input , search "password" , output : at the bottom - "No packet contained that string in its converted data"
		- STEP 4.4 : search "login"
			- output : <br>![[28_lecture-12-M3.jpg | 500]]
			- STEP 4.4.1 : right click on the "blue highlighted row" -> click on "Follow" -> 2 options will be shown <br>- click on either "TCP stream" or "HTTP Stream" : anyone option is fine - in order to see all the data packets ✔<br>- so click "TCP Stream" <br>![[28_lecture-13-M3.jpg | 500]]
			- now we're following getting Victim's system data packets via TCP stream
			- output : all the data packets captured <br>![[28_lecture-14-M3.jpg | 500]]
			- in output : section which are in red color = i.e request & blue section color highlighted = i.e response ✔ <br>- so firstly , we sent a request - then response came
			- STEP 4.4.2 : scroll down , uname & password<br>![[28_lecture-15-M3.jpg | 500]]
			- in output , password is not showing properly - cuz Victim didn't right the password correctly at the 1st time
			- STEP 4.4.3 : scroll down , "uname & password = test with HTTP status 200 ok" & session id in Set-Cookie Header<br>![[28_lecture-16-M3.jpg | 500]]
			- so this is how - MITM done
			- STEP 4.4.4 : close the Data packet pop
		- STEP 4.5 : remove "tcp.stream eq 3" & write "IP" - then select `ip.addr==192.0.2.1`
			- STEP 4.5.1 : see Source & Destination Columns <br>![[28_lecture-17-M3.jpg | 500]]
			- in Pic , <br>- when the data packet comes from Source (i.e server) to Destination (i.e Victim) <br>Source "44.228.249.3" = is a server's IP & Destination "192.168.186.142" = is a Victim's IP <br>- when the data packet go from Source (i.e Victim becomes the source) to Destination (i.e server becomes the Destination) <br>- Conclusion : Source & Destination flipped each other ✔
			- STEP 4.5.2 : write victim's IP , `ip.addr==192.168.186.142` & hit enter <br>- output : only details will be shown related to those 2 IPs
			- STEP 4.5.3 : now in "Find" input , search "login" , output : u'll get details instantly
	- this is how MITM implemented
- `imp Note ✅` : data packets details difference b/w websites running on HTTP & HTTPS
	- the website (which is used for practice) is running on HTTP <br>- so those websites which runs on HTTP - u'll get the data packets + u can understand data packets
	- but those websites running on HTTPS - u can capture data packets , but can't understand data packets <br>- cuz data goes in coding form <br>- so this is the security in HTTPS
	- Advice : everything has it's own loophole & security <br>- so the app , which has loophole - then security also available for loophole <br>- & the app , which has security - then security has it's loophole ✔

timeline 1:10:36 : [30-11-2023 - YouTube](https://www.youtube.com/watch?v=R0c_U-cNTlM)

---
### Homework
1. do data packets capturing on a HTTPS website (Eg : a website running on PHP) - in order to see what sort of data packets comes

---
### End of the lecture (Doubts) :
- Student's Doubts
	- Q : apart from LAN , is Session Hijacking possible in WAN ✔
		- Ans : to do Session Hijacking , Victim must be in our network of IP range
		- & Session Hijacking can't possible in WAN , it's only possible in LAN 
	- Q : to do Session Hijacking , is Victim needs to be connected in our network  ✔
		- Ans : so Attacker do ki either a attacker will connect to the Victim's router <br>OR a attacker allow Victim to connect in attacker's router/wifi
		- Eg : like in colleges , there are free wifi - so what if i go inside the wifi router <br>- then all those people (who're connected) will be hacked by u <br>- then u can capture their data packets
	- Q : let's say u're doing illegal activities - then the ur information will be accumulated by ur ISP/SIM-of-the-company <br>- then how can we make our system secure - so that we're not be trace by Cyber Police
		- Ans : there's no system/app/service which is full-proof 100% secure
		- so those who u do illegal activities - mostly they leave a trace/proof about their identify
		- Q : if u try to hack companies via their wifi router <br>Ans : it's not possible , cuz outside many companies - put firewall in their router <br>- so keeping a firewall - makes 99% secure - which we'll see in upcoming lecture <br>- but if firewall is not properly configured in their router - then after finding a way - we can enter in their router
	- Q : About : forensic in cyber security
		- Ans : means we try to recover data from a criminal phone/system (if he/she deleted or modified the data) <br>- & Forensic is a deep task - which includes recovering + analyzing
	- Q : is using a particular tool for long yrs - is fine
		- Ans : No , cuz this field is changing & new tools comes over old tools
		- so always keep in mind : if a tool not working for a particular task , then find alternatives of it
		- Advice from sir : tools like nmap has many things - which we just learned a little thing about it <br>- so follow self-learning + mentor teachings + dedicated path from Mentor
		- Advice : find a group & learn in a group - cuz u'll get support , doing self also fine <br>but having a group - then u can achieve ur goals properly
	- Q : till yet , what we have done
		- Ans : Ethical Hacking is 1st step in cyber security  <br>- & completing CEH - is like u just look ur admission in cyber security
		- so step by step - when u do practice - u'll get more clarity about a topic/subject
	- Q : which type of Job is good 
		- Ans : just only doing Remote Job - is not good <br>- take those jobs which are Hybrid (Remote + office) job
- Q : if network is not working properly 
	- like u ran `ping google.com` , output : ping of google is not showing again & again OR stuck at some point<br>- then means network is not working properly
	- run `service NetworkManager restart` -> then `ping google.com` , output : now ping will be shown again & again
- Advice : mostly b/w 2 systems - connection establish via SessionID
	- so hacking a person's social Media account without telling him/her = illegal
	- & even if he/she gave his/her account = then there's a chance that account is not of him/her <br>- cuz google , FB , instagram , etc gave u the permission & when these stuff allow u to give permission <br>- then only can hack otherwise not 

