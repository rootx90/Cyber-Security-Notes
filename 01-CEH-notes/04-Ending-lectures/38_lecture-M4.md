#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : Logs & Doubt Solve & Batch End
> 1) Theory : Logs
> 2) Practical Work : Logs

---
### Theory : Logs
- what's log
	- Eg : when u open ur phone & turn on screen - then unlock ur phone - then u perform ur tasks what u want to do <br>- so everything u do in ur phone from start to end = will be stored as log in ur phone
	- Log is like a history (of whatever things u do in ur device/phone)
- for what purpose , it's used / usecase of it ✔
	- Example : 
		- a attacker hacked ur system - then the attacker inserted a payload in ur system <br>& ur system might have 1TB storage or more/less than 1TB (which depends on victim)
		- now inside that big storage , there are many locations (like if u go inside C: drive - then u'll lost - same with other Drives) <br>- now to identify (where that payload inserted in which location + how the attacker inserted) - really difficult to for u <br>- but as earlier , we said that whatever things perform in ur system - will be saved as a log
		- so when a hacker - hack ur system - after hacked , hacker will take access of ur system <br>- then after taking access ur system , which location/folder he went to put that payload <br>Q : if that hacker will put that payload anywhere inside that big storage (of ur system) , will u be able to find that payload <br>Ans : No (cuz u don't even saw ur system's files & folders) <br>Q : will u be able to find that payload via scanning <br>Ans : No - cuz what if that payload is undetectable/encrypted - then how can find that payload via anti-virus <br>- so not possible to find the payload - that's why logs created in ur system
		- whatever that hacker did step by step <br>1st) he took the access of ur system <br>2nd) then he went to ur "file manager" app <br>3rd) then he accessed C: drive <br>4th) then "windows" folder <br>5th) then "config" folder <br>6th) then he finally put the payload <br>- so all these steps will be recorded step by step <br>Q : what we can do as a victim <br>Ans : we can follow these step by step - to delete that file <br>- that's why logs are used
	- sometimes logs get deleted due to security reason = aka covering tracks ✔
	- conclusion pic : <br>![[37_lecture-7-M4.jpg | 300]]
- Types of logs in WindowOS
	- 3 types of logs in winOS <br>1) system Log <br>2) Application Log <br>3) Security Log
	- in system log : <br>- all the logs (which are related to system) will be saved in system log <br>- Eg : how many storage is left in ur system , how much battery left , RAM storage left , <br>how much % of processor is getting use , whatever the services running (related to system) , etc
	- in Application Log : <br>- all the logs (related to application) will saved inside Application log <br>- Eg : which application was opened , when errors came inside an app , when changes done in an app , <br>when that application is installed , etc
	- in security Log : <br>- all the logs (related to security) will be saved in security log <br>- Eg : when did u unlock ur device , when did u write the password to unlock the device , <br>if a virus came in ur system - then anti-virus detected that virus & deleted it , etc
	- Conclusion Pic : <br>![[37_lecture-8-M4.jpg | 500]]

### Practical Work : Logs
- How to see logs in winOS
	- STEP 1 : search "event viewer" -> open it
	- STEP 2 : go to "Windows Logs" , output : different types of logs will be shown <br>- but major types of Logs are "Application , security , System"
	- STEP 3 : double click on "Application" , output : different sources will be shown (like Windows Error Reporting) <br>![[37_lecture-9-M4.jpg | 500]]
	- in output , at the bottom - u'll see details about that Source <br>- u'll see Event Name (means what's the name of it) of that source<br>- u can't open the link of "attached files" - due to security
	- STEP 4 : double click on "Security" , <br>- output : each security logs also got audited (means checking everything) <br>- eg : u'll see when did u unlock ur PC & locked ur PC , etc
	- to save a specific selected Events<br>1) select a event <br>2) go to "Action" tab <br>3) click on "save selected events"
	- STEP 5 : open "System" section - to see logs of system
- About "Covering Tracks" (means when hackers delete the logs to install something)
	- STEP 1 : in "Event Viewer" , go to "Windows Logs" -> "Application" -> on right side , click on "clear log" <br>- output : options will be shown "save & clear , clear"
	- STEP 2 : click on "Clear" , output : all the logs (of application) will be clearned <br>- but go to "System" , u'll see "Eventlog - log clear" <br>![[37_lecture-10-M4.jpg | 500]]
	- in output , see it's details 
	- STEP 3 : in System Log , clear all the logs of System , output : then still Eventlog will be created in "System" Log
- Clear Logs in Linux + winOS
	- in WindowOS :
		- so if hacker do same thing - then download a data recover tool : [Autopsy - Digital Forensics](https://www.autopsy.com/)
		- [ClearLogs AntiForensics | SourceForge.net](https://sourceforge.net/projects/clearlogs/) : <br>> About this tool : <br>- via using this tool to clear logs - then that person can't recover those deleted logs = that's why its Anti-Forensics tool ✔ <br>- Anti-Forensics : means a tool which can't be recover via Forensics <br>- we (as a cyber security) can't say that "impossible to recover deleted logs" - once those logs deleted via this tool <br>cuz there's no 100% surety <br>- as a attacker , once u got the complete access of a victim- then u have to clear logs properly
	- in Linux :
		-  STEP 1 : `sudo su` -> `/var/log` -> `ls` , <br>- output : all the saved logs will be shown (like "nginx" folder contains logs related to nginx , etc) , <br>"log" folder - contains all the logs (System , Application , Security)
		- STEP 2 : to clear , run `rm -r log *`
	- Advantage of clearing saved logs in KaliOS than windowOS : <br>- cuz its easier to access or delete them in Kali - but u still know nothing is 100% secure <br>- but Kali is more secure than WindowOS

---
### Homework
1. 

---
### End of the lecture (Doubts) :
- Advice : this Log is different than mathematics logs - whenever u learn new things then empty ur mind to grab new knowledge <br>- if u think that what if past knowledge will help in this topic - then that's the 2nd step of learning <br>- but currently just focus on present
- Q : define covering tracks <br>Ans : Once an attacker finishes his work, he wants to **erase all tracks leading the investigators tracing back to him**. <br>This can be done using. Disable auditing. Clearing logs.
- Students Doubt : 
	- Q : How we can bind any malwares behind an image or a vid , etc ✔<br>Ans : in [Module 07 Malware Threats\_zip.rar - Google Drive](https://drive.google.com/file/d/1xdheqnMP_V_CAfrZCOxwAAMooLm2-VNd/view) , see in "Malware Maker" <br>- u need search "How to bind a payload behind an image or a vid" <br>OR u can do like make a zip file & attach that payload with a zip file - & once the victim will extract - then that payload will execute <br>Q : worms or virus can be easily run after binding them behind an image or a vid <br>Ans : cuz work of (worms & virus) are not to take access - except damaging the victim's device <br>- & only in one click (worms or virus) can damage victim's device - so that's the easy task - cuz they only need to damage the device <br>- but to get the complete access of Victim's device - then big processes required <br>& can't possible to just bind any malware behind an image or vid
	- Q : define reverse-hacking <br>Ans : its like to find out the clue (about that hacker/victim) - going reverse/back from (end to start or start to end) <br>- just like in Logs , we did
	- Q : what if i use hardware (eg : wifi-adapter of a friend) & that friend also use it for penetration <br>- & its mac address also used somewhere - & if i use it - then will it create bad impact <br>- cuz if i use it - then my IP address will go with MAC address of it<br>Ans : Yes , but u also know "how to change the MAC add." - but still nothing is 100% secure <br>- u can use it - but if someone using black-hat-hacking via it - then cyber police will investigate <br>- tell me How many hackers comes in news frequently & even daily news doesn't showed on TV <br>those people will caught - if they did a big crime
	- Q : can we hack another system - via after hacking victim's system ✔<br>Ans : Yes , <br>Q : will my Main IP add. or details will go <br>Ans : No , but if u didn't take precautions/securities - then investigations will be done <br>- about , what that IP add. is doing in that Victim's system or in that another system <br>- & even Logs will be generated
	- Q : what kind of certifications can be done after CEH , for JOB <br>Ans : see 38 lecture vid - timestamp (1:08:19 - 1:15:01)
	- Q : which Linux OS is good ✔<br>Ans : <br>- for Beginners : Kali , Parrot (debian based linux OS)<br>once u learned about these 2 <br>- for advance users : Garuda (arch based linux) <br>once u learned about garunda <br>- move to "Black arch" (arch based linux) <br>- Black Arch Linux : is more powerfull - via it , u can hack satellite (but u required more powerful systems)
	- Q : how to hack CCTVs camera ✔<br>Ans : these have IP , so if any CCTV's IP address is in ur network range - then run scanning <br>- & if u find any open port - then come inside via that open port
	- Q : if 2 different ports open like HTTP & HTTPS in a website , then what kindof attacks possible <br>Ans : via both (HTTP & HTTPS) , we can send & receive the data <br>- our work is find out vulnerability , not to create vulnerabilites
	- Q : once this course completed - then what to do extra <br>Ans : do some stuff in deep like nmap , do the enumeration in windows 7, then try to hack windows (same process need to be done as like done linux) - we just need to find out exploits in windows 
	- Q : how to do website hacking <br>Ans : to learn about it properly , u need to learn & do WAPT <br>- mostly of stuff , depends on parameter <br>Q : steps to secure a website or a wordpress website ✔<br>Ans : <br>1) check whether firewall is properly configured or not <br>2) is any port open <br>3) test the website by its parameter (cuz even if firewall configured properly <br>- but mostly the time , parameters make the secure website vulnerable , so testing parameters is imp)
	- Q : what're the hardware & software tools for hacking <br>Ans : there are many (like for bluetooth - there's a hardware tool as well as software too) = same with others

