#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : Malware Analysis
> 1) Theory : what's Malware program
> 2) Theory : trojan
> 3) Theory : Virus & worms
> 4) Theory : Types of Malware Analysis
> 5) Practical Work : malware_threats.zip & legion(root) tool
> 6) Resources : 500 Books

---
### Theory : what's Malware program
- About : Malware
	- Malware - is a program which is not safe for our system
	- is a Malicious Software
	- Q : why is it made <br>Ans : to do damages or disable computer system
	- Q : what happens if it comes inside the victim's system <br>Ans : it can give limited or full control (which depends on situation)
	- Q : why is it use <br>Ans : to do theft or fraud
- Examples of Malware (Types of Viruses inside Malware)
	1. Backdoor
		- means malicious programs which run in backend/background of the system - to do malicious stuff 
	2. Rootkit
		- Eg : a tree has it's roots 
		- so programs which runs in root folders of a OS (in a system) <br>Eg : in WindowOS , root folders (like in C Drive : Bios , etc) - so these programs will go & stay on those folders <br>which makes difficult to scan
		- Conclusion : these programs will go & stay in deep of an OS (in a system) - to makes difficult for a user (to scan & remove them)
	3. Virus
		- it's made mostly for damaging the hardware - eg : connecting , disconnecting , disable 
		- it doesn't share any details - except to damage & corrupt the system (in terms of both Hardware + software)
	4. Worm
		- its made mostly to damage the software instead of hardware
		- Q : how it damage the software in a OS (of a system) <br>Ans : by spreading itself - just like coronavirus <br>- means once it's come in ur system - then it'll replicate itself to damage ur software <br>(due to this - at the end hardware also gets damage) <br>- it's a self-replicating program
		- it'll share information (of victim's system) - by self-replicating in a system
	5. Trojan Horse
		- Q : have u heard about RAT <br>Ans : RAT - Remote Access Trojan
		- Q : what does RAT do <br>Ans : it'll stay in a system - then it'll share/give a complete remote access to the Hacker = that's why called "remote access program"
		- Trojan Horse is a type of RAT <br>so it'll give a complete remote access (of the victim's system) to the attacker
	6. Crypter
		- it'll encrypt all the (files & folders) of the victim's system automatically
		- Q : when u download a software or a file , will that file/folder will be in encrypted form <br>Ans : No 
		- Even if that encrypted file contain a friend (like trojan , virus , etc) - it'll also encrypt that friend <br>- so that anti-virus can't read <br>Q : but now , anti-virus become more smart , what does they do <br>Ans : anti-virus see if that software/folder - contain normal files too (apart from imp files) <br>- & if those normal files are founded in encrypted form - then anti-virus doubt/don't-trust <br>- then anti-virus will start keep an eye on that folder/software
		- Q : u tell me that if someone hiding a normal thing from u - then will u doubt or not <br>Ans : Yes , cuz that's the normal thing & no point of hiding
	7. Ransomware
		- it's v dangerous + smart virus - cuz it has all the abilities of (backdoor , rootkit , virus , worm , trojan horse , crypter)
		- Ransom = means phirautee/फिरौती
		- when it come in ur system - then it'll encrypt all the files & folders (of ur system) <br>- & when u try to open any file/folder - then a popup comes (for "send 100 bitcoins" - mostly ask in bitcoins) <br>- & if u don't give the money - then they'll keep ur data encrypted

### Theory : trojan
- About : 
	1) malicious software
	2) Damages or disable computer system
	3) Gives limited or full control 
	4) predefined actions :  <br>- means Q : u want to open a phone/pc - then 1st thing what u'll do <br>Ans : unlock the device/phone - which is a predefine actions u're gonna do <br>- so same with trojan also contain predefine actions <br>eg : when u open the lock of ur device - then trojan will get active , when u press a button then it'll get active
	5) communication channel (Attacker & Victim) <br>- so that attacker can access victim's data
	- Conclusion : this is the way trojan works
- Common Ports used by Trojans ✔
	- pic <br>![[37_lecture-0-M4.jpg | 500]]
	- Q : what runs on Port no. 80 ✔<br>Ans : HTTP <br>- but if u see "codered" in the place of http - then means it's a trojan <br>- if u see "DarkFTP" running on Port no. 21 (instead of FTP) - then it's a trojan <br>- if u see "EliteWrap" running on Port o. 23 (instead of TELNET) - then it's a trojan
	- Advice : u should know well-known port no. - cuz names (of Trojan Virus) will change

### Theory : Virus & worms
> About : 
1. Infects Other Programs
2. Transforms itself : <br>- means change itself acc. to situations <br>- some viruses & worms are like once their work done - then they delete themselves from Victim's system
3. Encrypts Itself
4. Alerts Data
5. Corrupts files & programs
6. Self-Replication
7. File Downloads , Infected Disk , Email Attachments <br>- Q : from where these viruses & worms<br>Ans : downloading a unknown files , using infected disk (mostly on "cyber cafe") , email attachments

### Types of Malware Analysis
- 2 types of Malware Analysis <br>1) Static Malware Analysis <br>2) Dynamic Malware Analysis
- Static = fix , dynamic = changing
- About : Static Malware analysis vs Dynamic Malware Analysis
	- in Static Malware analysis
		- we can do malware analysis by ourself
		- Eg 1 : when we start the system - then can see what's running <br>Eg 2 : in our storage , what files there - which we didn't downloaded & automatically came
		- Eg : 3 : how many ports are open in our system & which ports - our system not using <br>Q : how to check which ports are open & which are not opened ✔<br>Ans : STEP 1 : in windows terminal , run `netstat` , output : u'll see <br>![[37_lecture-1-M4.jpg | 500]]
		- in "Foreign Address" column - means ports no. which are going , in "Local Address" column - are of own ports no. <br>- at the bottom total 5 ports are open in ur system <br>- Conclusion : Ports no. which are open & working - u can see for what purpose each port no. is open
		- "netstat" command - will not show services <br>- "netstat" - for windows & "man netstat" for KaliOS
	- in Dynamic Malware Analysis : Dynamic Malware Analysis done by anti-virus
- in Static Malware analysis 
	- Conclusion : we as a normal human don't do Malware analysis manually/statically - cuz these all done by Anti-virus <br>- but u should have knowledge about the process of How "Static Malware Analysis" done
	1. File Fingerprinting <br>- means collecting all the info about that file (eg : from where that file came , etc)
	2. Local & Online malware scanning <br>- there are many online malware scanning tools like [VirusTotal](https://www.virustotal.com/gui/home/upload) <br>so 1st scan the file on these sort of a website - then bring that file in ur system
	3. Performing string search <br>- means in a unknown file , search for those words (which are giving remote access or establishing a connection) <br>- eg : in a unknown file , search words like "LHOST , LPORT , etc" <br>- so all these performed in "string search"
	4. identifying Packing / Obfuscation methods <br>- eg : in a system , if any local file encrypt itself automatically - then figure out why that file/folder keeping itself encrypted form <br>cuz if that file/folder is in a system locally <br>- its also done by anti-virus but we (as a user) check manually
	5. Finding the portable executables (PE) information <br>- means if a file downloaded in portable executable (i.e .exe) automatically or it came with a another file (which downloaded) <br>then identify what kind of permissions , services , dependencies , from where it came from OR somebody one put it in ur PC OR <br> is it already been in ur PC  <br>- these are stuff u need to see
	6. Identifying file dependencies <br>- means what are the things that unknown file have Eg : what kind of dependencies it requires , etc <br>- due to this , we need to see whether it's taking our main's system dependencies or not <br>- Eg : sometimes happen that a unknown program requires "C Drive" for installation & then only that unknown file will execute ✔
	7. Malware Disassembly <br>- if u know programming - then read that file + disable it , etc
	- Conclusion : all these things can't be done by a normal human - that's why anti-virus made
- Stage of Dynamic Malware Analysis
	- 2 stages of it <br>1) System Baselining <br>2) Host Integrity Monitoring
	- intro : System Baselining & Host Integrity Monitoring
		- System Baselining <br>- means system do malware scanning without any external anti-virus <br>- even now system has it's build-in anti-virus
		- Host Integrity Monitoring : <br>- monitoring of Host done <br>- Eg : someone take the access of a system , then the system (of the victim) will see/check who's that unknown host <br>lets say IP address of victim's system is 122.168.2.4 & if a unknown access entered in ur system <br>then ur system will check/see/analyze who's that unknown access = aka Host Integrity Monitorning
	- System Baselining vs Host integrity monitoring
		- pic : <br>![[37_lecture-2-M4.jpg | 500]]
		- "snapshot for changes" <br>- means if u're building ur physic & to see changes of ur "before" & "after" <br>then what u'll do - u'll capture photos/snapshots <br>- so same both capture photos to (see + compare) changes <br>- Eg : like earlier how many ports were open & now how many ports are open , etc
		- in system Baselining , <br>> file system : means how & what kind of permissions "file system" has - means checking details all about "file system" <br>> registry : <br>Q : what's registry ✔<br>Ans : whenever any service start - before starting , a registry is done <br>- means system note-down a registry about which service is going to start <br>> open ports : means how many ports are open & earlier how many ports were open <br>> then "Network Activity" : will be checked <br>- eg : everything related to network - will be checked like how many traffic u have in ur system , how many ports are open
		- in Host integrity monitoring , <br>- everything will be checked in details <br>> Port , Process , Registry , Windows services , startup programs : <br>- means all of these earlier how many they were running & now how many they're running <br>> Event logs , Installation , files & folders : <br>- Event logs - means how many logs are added , is any logs deleted or not <br>- Installation - how many installation done , earlier how many installation were exist <br>- files & folders - files & folders will be checked about what kind of permissions files & folders have <br>& which permissions has been added newly <br>> Device Drivers , Network traffic : <br>- which device drivers are added extra & how many traffic in ur network <br>- Eg : let's a extra driver in ur system & it contains virus or a software is a virus - & it sending data continuously <br>then ur network traffic becomes more = that's the malicious application ✔ <br>> DNS , API calls monitoring : <br>- Q : define API <br>Ans : Application Programming Interface : means a website which is a interface & that interface made via Programming <br>so when u enter in a website - then 1st u enter inside or call that API or u enter inside that website's database<br>(means until u don't see API OR - then u wouldn't able to understand) ✔<br>- means what kind of APIs did u accessed/call - will be monitor by "Host Integrity Monitoring"
		- Conclusion : these all are a process of Anti-Virus

### Practical Work : malware_threats.zip & legion(root) tool
- STEP 1 : open task manager -> startup apps , disable those apps which are not required
- malware_threats.zip
	- STEP 1 : go & download this : [Module 07 Malware Threats\_zip.rar - Google Drive](https://drive.google.com/file/d/1xdheqnMP_V_CAfrZCOxwAAMooLm2-VNd/view)
	- Password : 784512
	- STEP 2) don't extract it . just open it via 7zip or winzip , output : viruses folders that u learned already
	- Advice : <br>- don't use them in ur main system , in virtual machine , download windowOS & use them <br>- Note : whenever use them - 1st turn off all the anti-virus <br>- do this experiment in Windows 10 (cuz these malware threats won't work properly in Win7 OS)
	- STEP 3) click "Trojans Types" folder -> click "HTTP HTTPS Trojans" -> click "HTTP RAT TROJAN" <br>- output : httprat.exe & httpserver.exe <br>- httprat.exe = is a main file - means attacker will keep it on its PC & httpserver.exe = will go to victim's PC ✔<br>- once we use it then we'll get remote access of the victim's system
	- u'll also find keylogger in "HTTP RAT TROJAN" - if u don't find keylogger then no need to worry
	- Q : is this "Malware Threats" file also work in android <br>Ans : No , cuz it's not for android
	- for it's practical - see the 38 Lecture vid : timestamp ( 38:02 - 46:45 )
- legion(root) tool
	- advantage of this tool : u can many task inside this tool - instead of going in different tools (like nmap , etc)
	- STEP 0 : open both Kali & metasploitable2
	- STEP 1 : in kali , search "legion(root)" -> "kali" password , output : it'll get open
	- STEP 2 : go to Hosts -> click on "+" btn -> then IP address (of metasploitable2) on that empty box <br>![[37_lecture-3-M4.jpg | 500]]
	- STEP 3 (optional) : in "Mode selection" , u can select acc. to ur needs
	- STEP 4 (optional) : u can select all the options acc. to ur needs
	- STEP 5 : click "submit" btn , output : u can see Services too
	- STEP 6 : click "smpt" 25 port no. , output : <br>![[37_lecture-4-M4.jpg | 500]]
	- in output , those options means what're the ways via which u can open that protocol <br>Homework : try it by urself - cuz u can do majority of stuff from this tool (instead of using different tools for different tasks)
	- STEP 7 : in Hosts -> select "ftp" protocol -> right click & click "open with telnet" <br>![[37_lecture-5-M4.jpg | 500]]
	- output : u'll get direct access but just only give username & password of that victim's system (i.e metasplotable2)<br>![[37_lecture-6-M4.jpg | 500]]
	- `Note ✅` : if u open via wrong protocol - then "protocol mismatch" error come <br>- cuz u can't open FTP via telnet - only telnet can be open via telnet ✔
	- STEP 8 : close the terminal pop -> select telnet protocol -> right click , "open with telnet" <br>- output : u'll get complete system access of victim (i.e metasploitabl2)
	- Conclusion : u can do most of the stuff inside this tool
	- `imp Note ✅` : victim's system should be in range of ur IP address (of ur system) <br>OR that victim's IP address must be Public IP (just like website's has Public IP address) <br>- any one of the situation must be fulfilled to do scanning of victim's system

### Resources : 500 Books
- Q : which one to read <br>Ans : read those books which u think that it's required + necessary acc. to ur knowledge level , leave the advance
- Download Link : https://drive.google.com/file/d/1xxZzXXK2YyKjcXEgnHUyfM8MC5W7Q4D0/view
- Advice : <br>- acc. to u "what u don't know or u think that topic is weak" - then pic that book <br>- HackersPlayBook - is good <br>- if u getting understanding via books - then refer YTchannels related to that

---
### Homework
1. 

---
### End of the lecture (Doubts) :
- Q : About : API <br>Ans : https://www.perplexity.ai/search/what-is-api-60yHBWFdS.SuYUDKpB6DfA
- Q : About : Virus & Worm
	- Q : difference b/w virus & worm <br>> https://www.cyberghostvpn.com/privacyhub/wp-content/uploads/2021/06/Virus-vs-Worm@2x-1-1024x720.png <br>> [Difference between Worms and Virus - GeeksforGeeks](https://www.geeksforgeeks.org/difference-between-worms-and-virus/)
	- Q : which one share information about the victim's system Virus or worm <br>> [Ans 1](https://www.perplexity.ai/search/which-one-share-TFvgyICdRCKFymvyXP6hVA?s=u) <br>> [Ans 2](https://www.perplexity.ai/search/which-one-share-9lheZjUITwOJY8zUh.pELw?s=u)
	- Q : is virus also self-replicate program to damage the victim's system <br>> [Ans 1](https://www.perplexity.ai/search/is-virus-also-8dV9T3W5TP6b1Zet9lrp.w?s=u)
	- Q : is virus or worm which one is better <br>> [Computer Virus vs. Worm: What’s the Difference? | Avast](https://www.avast.com/c-worm-vs-virus) <br>> Ans : Usually, **a worm is more dangerous than a virus**, because it can spread more quickly. <br>For example, a worm could infect all of your email contacts. <br>> 
	- Q : Malware vs. Worm vs. Virus & which one is more dangerous <br>> [Malware vs. Virus vs. Worm: What Is the Difference? | Fortinet](https://www.fortinet.com/resources/cyberglossary/malware-vs-virus-vs-worm)
- About : in Dynamic Malware Analysis , System Baselining & Host Integrity Monitoring
	- Q : what is the purpose of system baselining in dynamic malware analysis <br>> [Ans - Purpose of it](https://www.perplexity.ai/search/what-is-the-HCe42.eeQbaa5oi14XzAfA?s=u)
	- Q : More on - System Baselining & Host Integrity Monitoring <br>>  [System Baselining & Host Integrity Monitoring](https://www.perplexity.ai/search/in-Dynamic-Malware-gLE6CYg6ReGhHQLDgNpApg?s=u)
- via nmap - websites scanning also possible ✔
- Students Doubts
	- Q : why redirect way used for the website <br>Ans : redirect way used send the user to the alternate official website (of main website) if that main website not working <br>- Advice : 1st check whether that redirected website is safe or not
	- Q : is trojan will work on linux <br>Ans : No , cuz structure of Linux is different than WindowOS <br>- but u can only if u know programming <br>- same with android - cuz 1st u need to understand structure of AndroidOS - then u can create trojan for androidOS
- Advice : don't install win10 OS for testing in virtual machine - cuz it's very old , use win11