#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : Hacking Mobile Platforms
> 1) Theory : intro
> 2) Theory : Mobile Platform Attack Vectors (Vulnerable Areas)
> 3) Theory : OWASP Top 10 - Mobile Risks - 2016
> 4) Theory : Mobile Platform Vulnerability & Risks
> 5) Theory : Mobile Security Guidelines

---
### Theory : intro
- Hacking Mobile platforms : means whatever the ways where attacks & viruses come in mobile

### Mobile Platform Attack Vectors (Vulnerable Areas)
- Pic : <br>![[35_lecture-0-M4.jpg | 500]]
- in pic , that spikes ball = Vulnerable area
- Explanation : Mobile Platform Attack Vectors
	1) Bluetooth
		- in ur phone , if keep bluetooth ON always - then virus can come
		- Q : do u know what we were doing with bluetooth - when headphone was not in the market <br>Ans : file sharing , data sharing
		- so if u keep ur mobile's bluetooth ON - then file sharing + data sharing could be possible <br>& data could be shared & receive
		- so if someone hack ur mobile's bluetooth via RF Hacking - then data sending/receiving would be possible (including virus)
	2) Wi-Fi Device
		- root cause of viruses = aka internet - cuz everything is connected with internet <br>eg : wifi-device , appstore , websites , telco service provider <br>- means if u're connected with internet - then there's a chance that virus will come from anyway
		- if u're connected with a wifi-device (which is unknown or free-wifi) - then MITM , etc attacks can be performed
		- Advice : that's why always be careful before connecting to any wifi & that wifi's password should be strong <br>- & avoid (as much as possible) connecting to any public wifi - cuz might that public wifi running by a group of hackers
	3) App Store
		- there're less chance that installing any app from appstore
		- But don't download any APK , 3rd-party store
		- Eg : if u use oppo , Mi , etc phones - which have 2 playstore <br>1) playstore of google <br>2) playstore of that phone <br>- don't use playstore of that phone - to install any apps
	4) Internet : we already seen - root cause of viruses/attacks happens on a device via internet
	5) website
		- already saw social engineering (means making a fake website) to get the Victim's login details
		- if u go on those websites (which are not secure) - & click on anywhere - then might be chance i.e directly virus can come
	6) Corporate VPN gateway + Corporate Intranet
		- Corporate networks are little bit secure - cuz in corporate , firewalls are configured properly + different internal VPNs used <br>+ different gateways also used
		- Gateway = means 1st way to move <br>eg : our router's gateway is 192.168.1.1 = means by-default 1st IP address of the router aka gateway ✔ <br>- means packets send/receive via that by-default 1st IP address of the router
		- in corporate Intranet , <br>- corporate setup their own internal modems & routers with properly configured <br>- that's why Corporate people able to connect to internet securely - due to this virus can't come easily (cuz things are scanned via firewall - before entering inside corporate's devices)
	7) Telco Service Provider / mobile towers
		- RF attack can be possible in Mobile towers
		- one more vulnerability in Mobile Towers - Q : have u called someone via phone no. <br>Ans : Yes , but sometimes it's happen to u i.e when u call someone via that phone no. <br>- but sometimes other's person voice come = aka miss-connection 

### Theory : OWASP Top 10 - Mobile Risks - 2016
- for more : [OWASP Mobile Top 10 2024](https://owasp.org/www-project-mobile-top-10/)
- Explanation of OWASP Top 10 - Mobile Risks - 2016
	- M1 : Improper Platform Usage
		- Eg : phone contain features like camera , fingerprint , password , etc , <br>Q : when u open ZOOM - then is by-default ZOOM takes fingerprint <br>Ans : No , so same with whatsapp also <br>- means ZOOM is using some features & some not of a phone - but features (which are not used by ZOOM) <br>same way - there are some apps (which uses all the features of the phone) & some apps (which use some features of the phone) <br>- means in ur home , there are 4 doors - but u only use one door for exit/enter at home
		- Conclusion : a device has more features = more vulnerabilities <br>- that's why Apple phone has limited features - than android ✔
	- M2 : Insecure Data Storage
		- Eg : in phone , whatever u download - those downloaded stuff stored inside "Download" folder <br>- & ur photos are stored inside "Photos" folder , etc <br>- so if someone take ur phone , then the person can access ur everything inside ur phone
		- even all those data (which are stored in their respective folder) are not encrypted <br>- means if a person take ur phone - then he/she can easily see the data
		- means a phone is not using storage system securely <br>even those files/folders accessible via writing path of that folder/file in chrome browser ✔
		- so Phone's storage system is also not secure
	- M3 : Insecure Communication
		- eg : we already talked i.e when we call to a person - but a different person's voice come = aka miss-connection
		- & due to this vulnerability , MITM attack also possible - means a middle person watching/listening the victim's voice
	- M4 : Insecure Authentication
		- eg : u're sleeping & a unauthorized person using ur fingerprint to unlock ur phone = insecure auth
	- M5 : Insufficient Cryptography
		- means Cryptography is getting used only for few stuff (like password) - but not for other stuff
		- means Cryptography is used only to encrypt password - but it's not used to encrypt other sensitive stuff
	- M6 : Authorization
		- same as M4 
		- Eg : let's say a person gave u the password of his/her own wifi - but again 2nd time , u meet that person <br>- u didn't asked for password & u started using his/her wifi <br>- so u're not authorized - but u can still use wifi via the password
	- M7 : Client code quality
		- quality of writing code for front-end - is not secure
		- Eg : when u download ZOOM , etc apps in ur phone - then code (of a application) stored in encrypted form in the phone <br>- which we'll see in WAPT
		- Conclusion : security of code is not good of a app/webapp
	- M8 : Code Tampering
		- Tampering = aka doing changes
		- means if security of code - is not good - then we can write malicious code
	- M9 : Reverse Engineering
		- if we're able to write malicious code in a app/webapp - then we can do reverse engineering too
		- means we can create a clone (with malicious code) of that same app
	- M10 : Extraneous Functionality
		- means having extra functionality/features (which are not useful) in phone <br>more features = more vulnerabilities

### Mobile Platform Vulnerability & Risks
- already seen above - Theory : Mobile Platform Attack Vectors (Vulnerable Areas)
- Explanation : ways from where viruses , attacks can come in the device
	1) Malicious Apps in Stores
	2) Mobile Malware
	3) App Sandboxing Vulnerabilities
	4) Weak Device and App Encryption
	5) OS and App Update Issues
	6) Jailbreaking & Rooting
		- both words means same 
		- Jailbreaking = used in IOS <br>Rooting = used in Android
		- if someone trying to do rooting/Jailbreak in ur phone - that's mean - that person taking full control over ur phone
	7) Mobile Application Vulnerabilities : no app is 100% secure - just like Dettol soap can't kill 100% bacteria
	8) Privacy Issues (Geolocation) : mostly apps ask for location or camera , photos access
	9) Weak Data Security
		- Eg : in windows , we saw where passwords of each type of users stored in a file in encrypted form
		- Homework : see on which location where passwords are saved & stored in encrypted form in phone
	10) Excessive Permissions
		- means an app (which doesn't need those extra permissions)  also took those extra permissions
	11) Weak Communication Security
	12) Physical Attacks
		- Eg : u're in railway station , & u were using charger (which might behind the scene - contain "rubberducky" program) <br>& that hacker can take away ur data or send virus in ur phone
		- so physical attacks would be possible
		- Advice : never use outside chargers , carry power bank to charge ur phone

### Mobile Security Guidelines
1. Enable Screen Locks
2. Never root ur android device
3. Download apps only from the official Android market
4. keep ur device updated with google android anti-virus software

---
### Homework
1. 

---
### End of the lecture (Doubts) :
- Student Doubts
	- Q : can crack app/tool fine to use <br>Ans : No , cuz cracked apps/tools are made by hackers
	- Q : a student's android & iphone - both devices go hacked & he/she is looking into Google Account Manager in Gmail <br>& he saw unknown settings - he's saying i.e "it's a part of social engineering" - then his phone got compromise ✔
		- Ans : Q : sir asked from that student : how do u know that ur phone got compromise
		- student replied : he's trying to recover his data & he saw a .json file & then suddenly everything getting stared deleted
		- Student replied : he has 3 devices with same gmail logged in <br>& he's trying to reset the phone - then he saw threats/dhamkiya messages
		- sir said : if ur gmail account got hacked then there are 2 things <br>1) change ur gmail password completely + Turn On 2FA <br>2) if ur phone got hacked - then don't try to take single backup from ur phone <br>(if already took backup then remove all the data) - cuz u don't know where that hacker put the virus <br>- & if u think that some data are imp to u then upload those data on Drive only ,<br>then do a complete system scan via QuickHeal-AntiVirus
		- Student replied : he saw 2 IPs - which is blocked by firewall + antivirus
		- Sir said : did u find any virus after doing complete system scan <br>student said : no , he use mcafee anti-virus
		- Sir said : sometimes anti-viruses also showoff in a way that "we're working" <br>Student asked : in android/iphone phones , is payloads can be checked <br>Sir asked : did u visited any unknown websites <br>Student replied : no
		- Sir asked : do u use this system - to do practical <br>Student replied : Yes <br>Sir said : that IPs are of Ngnix <br>Sir said : go to main system's firewall settings -> then close the incoming networks , only keep outgoing
		- STEP 1 : at bottom right , go to connected wifi icon <br>STEP 2 : click on properties <br>STEP 3 : under Network profile , select Private (instead of public) - cuz it makes system secure<br>STEP 4 : click "Configure firewall & security settings" , u'll see all securities ON & try to "u shouldn't turn off ur firewall"
		- Sir said : do a complete system scan via QuickHeal - cuz Mcafee not good (might it's going fake notification)
		- Sir's Advice : never connect to a unknown network ✔
		- Kishan (student) said : when his all the devices (android , iphone , lapi) got hacked - then automatically <br>browser got opened & suddenly 20-25 tabs opened - & each tabs were downloading something automatically
		- Sir said : that hacker got ur email accessed or that hacker might installed a payload in ur system 
		- Sir asked : is anything happening to ur phone <br>Kishan said : in iphone (he didn't took any backup) - but automatically hostpot got ON & when he do switch off <br>then switch ON automatically
		- Sir said : use Quickheal to scan ur phone <br>- don't use mcafee - cuz sometimes anti-virus contains virus within itself
		- Kishan said : if somebody put payload in our PC - then can we check his/her connection - mean can we track <br>that person to know who's is tracking our PC  ✔<br>sir said : Yes , by using wireshark <br>Kishan Said : i am letting my pc to compromise - then i'll track - is it possible to track ✔ <br>Sir said : yes , tracking possible
		- Sir said : search for unknown stuff only
		- Sir said : if u use kali , then it's not easy to hack a linux OS <br>u can use Dual Boot way to run 2 different OS 
	- Q : can i use free proxies or cracked proxies to hide the actual IP of the internet
		- Ans : No , cuz even cracked proxies - make u more vulnerable
		- might be there's a chance that a hacker made those free proxies - which u're going to use
		- use paid proxies or trusted proxies only
	- Q : if a person connected to ur fake wifi - then can we install malicious stuff on that person's device ✔
		- Ans : once u got the complete access of that person's device  - then u can install anything in that device
		- via both MITM , fake access point , we can only see details (like gathering small info) of victim's device <br>- but to install anything inside Victim's device - u need complete access of that device <br>& this wouldn't possible via Session Hijacking - but like that victim sharing a info via device (like loggin inside google) <br>then u can take his/her password
		- like u can't take remote access of victim's device via just creating direct fake access point <br>- cuz via Fake access point , u'll get only little small details about victim & u can also monitor that device<br>- details like (what victim is searching , etc)

