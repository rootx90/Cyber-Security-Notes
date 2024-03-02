#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : Web Server Hacking using ZAP
> 1) Explanation by Sir - About : Web Servers Vs Web Applications
> 2) About : web server + it's attacks + attack Methodology
> 3) About : Web Application + WebApps Hacking Methodology
> 4) Practical Work : Website Attacks

---
### Explanation by Sir - About : Web Servers Vs Web Applications
- Advice : we'll not go in deep about the Topic - cuz it's a part of WAPT <br>- so we'll try to find out vulnerabilities only
- More About it : 
	- [What is Web Application (Web Apps) and its Benefits](https://www.techtarget.com/searchsoftwarequality/definition/Web-application-Web-app)
	- [Web Server vs Application Server - YouTube](https://www.youtube.com/watch?v=BcmUOmvl1N8&ab_channel=DurgaSoftwareSolutions) <br>> [Web Server vs Application Server | by Louannracquelabove | Jan, 2024 | Medium](https://medium.com/@louannracquelabove47/web-server-vs-application-server-10cd3f4f52c1)
	- [WHAT IS WEB APP | Websites Vs Web Applications | Web Based Application - YouTube](https://www.youtube.com/watch?v=lYbATjjjDxM)
	- [Difference Between Website & Web Application - Hindi - YouTube](https://www.youtube.com/watch?v=E4PPD9lzQlg) ✔
	- [Web Server vs Application Server vs Web Container vs Web Application: A Comprehensive Comparison | by MEsfandiari | Medium](https://medium.com/@mesfandiari77/web-server-vs-application-server-vs-web-container-vs-web-application-a-comprehensive-comparison-2ee1a18313af) ✔ 
- Web Server ✔
	- Q : what's a Web <br>Ans : means a website <br>Q : what's a server <br>Ans : a server which has more (configuration + storage) - than a normal system
	- Eg : a client system & a web server
		- Q : when u open a website - then behind the scene - what processes happen<br>Ans : let's say u searched wscubetech.com <br>- now from the client system , a request packet will be generated <br>- that request packet will go to the server <br>Q : inside the request packet , what details are inside <br>Ans : we already seen like who's sending this request packet , etc..
		- once the server verified the request packet & the client system asking for legal stuff <br>- Eg : asking for the "wscubetech.com" website - then the web server will give a reply (as response packet) to the client <br>i.e a complete page of the website (means a complete coding of the website)
		- but if the client system - asks for admin page - then the web-server will not give <br>- cuz it's not allowed to give "admin page" to the client
		- so whatever u do in the website - those request packets processes handled by the web server , not on client system ✔
		- Q : there are online light games websites , so how processes (of sending & receiving data packets) done ✔<br>Ans : so all those games processes performed on the web server - cuz those games are very light to play on website
		- Q : if we play pubg , freefire , etc heavy games on websites (on client) - then where all processes load comes ✔<br>Ans : so if we play these heavy games on websites - then all processes loads comes on the web server <br>Q : after this , what'll happen - if many people of each country started playing these heavy games on websites ✔<br>Ans : countries like india , UK , etc : lakhs of users started playing these heavy games on websites <br>- then there's no server created yet - which can handle these heavy processes of heavy games & requests of all users
		- so there's no powerful server made yet - to handle heavy processes of all users <br>- so servers can't handle heavy games processes
		- so web servers only work to handle request & response <br>- Eg : uploading something , searching something , etc - for basic stuff , <br>- so web servers can handle requests & response for basic stuff
- web application ✔
	- sir thoughts on Web Apps concept
		- Eg : a client system & a web server <br>- so in concept of Web Server , whatever operations we were doing on the client system <br>then all processes happening on the server
		- Eg : if u want to play PUBG , GTA , etc heavy games <br>Q : where u download these heavy games - means do u play these games on websites or download in system <br>Ans : System/phone <br>- so the game which u downloaded from the website - i.e web application
		- & connection stuff like u're in pubg : reviving a teammate , shooting , collecting , communicating with mic , etc <br>- all these activities of connecting each other - are done by web server , but all the major processes done in client system ✔
		- Eg : GTA is a heavy game , so all the major processes & loads performed in client system ✔<br>- but like u're writing cheatcode (eg : bringing a tank) & code of tank is already in client system <br>so once u write the cheatcode of tank - then only response will go to the web server <br>- & the web server will activate it in client system <br>- so that's the little response & request (handled + performed) on the web server ✔
- web apps concept learned deeply in WAPT field <br>that's why - we'll do practical of Web server , not web apps
- so we'll see different types of vulnerabilities of Web Server & Web Apps

### About : web server + it's attacks + attack Methodology
- What's web server
	1. Computer System : means it's a computer system
	2. Stores : means it's a computer system where it stores more data
	3. Processes : it process the request data packets
	4. Delivers web pages : it delivers web pages based those data packets
	5. To client via HTTP/HTTPS : it delivers web pages to client system - via HTTP/HTTPS <br>- so when data comes from client & data sent by server to client - done via HTTP/HTTPS
- Web Server Attacks
	- DOS/DDOS attack : we did it via burpSuite
	- DNS Server Hijacking : means session Hijacking
	- Directory Traversal Attack :
		- Q : what's it & how were we doing it <br>Ans : Q : have u seen "`Indexof:`" : means due to it , we were able to access files & folders of FB
		- means if a website has a "`Indexof:`" vulnerability - that's called Directory Traversal Attack ✔
	- MITM attack : we did this via Tools i.e Ettercap & WireShark
	- Phishing Attacks : we'll see in Social engineering Topic
		- Eg 1 : we also did phishing via camphish tool
		- Eg 2 : amazon is a website - then u (as a attacker) made a clone of amazon website <br>- he/she didn't made the complete website - he/she just made a template (which just looks like amazon) <br>- & when u share the clone website to anyone - then for that person - clone website looks like real website <br>- & when that person fill credentials - those details comes u aka i.e phishing ✔
		- Phishing Tools : [phishing tools for kali linux](https://www.perplexity.ai/search/phishing-tools-for-4mbSkXf9RJ2N60rf8rwuCQ?s=u)
	- Web server Misconfiguration : 
		- this vulnerability created by those users - who hosted their websites details on server
		- Eg : when u brought a new router - that router has already a by-default password to login <br>- so a attacker has a list of default passwords of router , so any attacker can access that default password <br>- so if u don't change the default password <br>means u didn't changed the default password - that's considered as Misconfiguration ✔
		- so same happens on Web server - like a person who's running that web server <br>- if he keeps the default settings/configuration as it is of the web server - aka Web Server Misconfiguration ✔ <br>- that's why hackers able to hack the web server
	- Web Cache Poisoning Attack : 
		- it's done on either a website or a server
		- a attacker see old cache (via "cache:" operator) of a website or a server - then he/she will extract all the details <br>- then he/she will check what sort of updates/changes done - then he/she will find vulnerabilities <br>- after getting vulnerabilities - he/she will do poisoning & try to hack the server OR website itself <br>- so if either a server or website hacked via cache poisoning on it = aka Web Cache Poisoning Attack ✔
		- Eg : u used "cache:" operator on wscubetech website
	- SSH Brute Force Attack : 
		- Brute-Force attack done on SSH <br>Q : how Brute Force attack done on SSH <br>Ans : via username & password of SSH
		- Note : mostly password stored in Hash form ✔ <br>we'll see more about Hash - when we do password hacking 
		- Eg : a attacker wants to crack the password of a phone <br>- as password stored in Hash form - & that hash can't be decrypt - cuz the hash works in 1 way , not 2 way ✔<br>- so when a attacker try to crack the password via taking password list - then he/she will do Brute Force attack step by step <br>- & once the hash (of password word list) gets matched with actual hash password - then phone's password can be cracked ✔
		- so each hash password (of password word list) tried by a attacker - to crack the phone's password = aka Brute Force <br>- Eg : like many different attacks done - to access many directories of a website <br>so doing many different attacks at the same time = aka Brute Force  <br>- means doing many different attacks = considered as Brute Force attack ✔
	- Web Server Password Cracking : means cracking password of a web server
	- SSRF (Server-Side Request Forgery Attack) : 
		- is a part of WAPT
		- Eg : a user currently - login own his FB account - & u (as a attacker) want to delete ur own FB account <br>- in FB , there's a ID given to every user - so that FB server able to identify each user <br>so ur ID no. = 123 & that user's FB ID no. = 456<br>- so u'll generate a request to delete ur account (Note : without generating request - u can't delete the website) <br>- so firstly , u'll create a delete request - then the FB server will reply with ur ID no.<br>so till yet - u generated a request - but u're not deleting ur FB account <br>- so Now u'll put that user's FB ID No. on ur FB ID no. - & u'll send deleting FB account request to that user ✔
		- Q : u generated a request for deleting ur FB account - Now u're putting that user's FB ID instead of putting ur FB ID no. <br>What'll happen Now ✔<br>Ans : when u send the link (of deleting FB account with that user's ID no.) to that user <br>- & once that user clicked on link - then that user's FB account will get deleted completely
		- aka SSRF attack
- Web server Attack Methodology
	1. Information Gathering + Web Server Footprinting : these 2 things firstly done - to hack a web server
	2. Website Mirroring : means making a clone (of that actual website) with a different address
		- in Cyber Security , there's a saying that if a phone/website/apps/lapi contain more features = more vulnerabilities <br>- means having more features in a hardware/software = more vulnerabilities ✔
		- that's why - as a ethical hacker - we see all the things in a website includes it's each pages
	3. Vulnerability Scanning : means what are vulnerabilities in that website + what vulnerabilities might be possible
	4. Session Hijacking : 
		- firstly , we (as a Cyber Security) try to find whether that website has "Session Hijacking" vulnerability or not <br>- if the website has this vulnerability - then we'll perform Session Hijacking ✔
		- Otherwise , not performed
	5. Web Server Password Cracking : means if possible - then we (as a Ethical Hacker) try to crack the web server password 
	- Conclusion : these are methods - which are used to hack the web server

### About : Web Application + WebApps Hacking Methodology
- it's a part of WAPT , so we'll not study deeply 
- A Web Application has :
	1. Interface
	2. End user (client)
	3. Web server
	4. Client Side Script (Browser) : <br>- means all the interface/code of a website are on Client side , a web server just handle request & response <br>- Eg : currently u're taking live class on Zoom , in encrypt form - all the source code of ZOOM will be in ur system (i.e client) <br>- in WAPT field , u'll learn - in client system - how to decrypt those source code of an app 
- WebApps Hacking Methodology
	1. Footprinting Web Infrastructure
	2. Analyze Web Application
	3. Bypass Client Side Control : 
		- Eg 1 : 2 users i.e Admin user & Guest user - so Guest will try to bypass authority of user (who's a admin)
		- Eg 2 : a attacker (as a client) - not able to see details of that server (which is not allowed to see) <br>so that attacker will try to bypass security of the server - in order to see deep details
		- is a part of WAPT
	4. Attack Authentication Mechanism
	5. Attack Authentication Schemes
	6. Attack Access Control
	7. Attack Session Management Mechanism
	8. Perform Injection Attacks
		- there are many Injection attacks Eg : SQL-injection , etc
		- Eg : whatever attack we're perform - we (as a attacker) inject that attack on that web app - then we see what's happening <br>on that webapp = aka Perform Injection Attacks

### Practical Work : Website Attacks 
> Overview : we'll see some website attacks via using Automation tools i.e ZAP proxy & another tool : Acunetix
- STEPS : Practical Work - Website Attacks via Zaproxy tool
	- About Tool : 
		- we say "ZAP proxy" - but we write "ZAProxy"
		- made by OWASP (Open Web Application Security Project)
		- Q : what OWASP organization do <br>Ans : this organization - analyze vulnerabilities of 2-3yrs (of everything like phone/lapi/website/app/technology) <br>- then release TOP 10 biggest out of those vulnerabilities + security for each vulnerabilities
		- it scans both HTTP/HTTPS websites ✔ <br>Advice : don't do scanning on HTTPs websites like wscubetech - cuz it'll get down if u do
		- said by Sir : 
			1. both hacker & developer get the benefits of TOP 10 biggest vulnerabilities + security for each vulnerabilities <br>- means Developer able to fix those issues - but if any vulnerability left or again created <br>- then due to this , hacker got the benefit
			2. actually Developer also don't know those stuff - whatever things we learn as a Cyber Security <br>- at the end of the day , developer's app/website contains many vulnerabilities <br>which u (as a Cyber Security Beginner) don't know
			3. Think About it : what if firewalls removed/shut-down from every website - then all the websites will be hacked everyday <br>so having a firewall in each websites - makes the website protected <br>- later we'll learn : Firewall configurations
	- STEP 0 : `sudo su`
	- STEP 1 : `zaproxy` -> then press "y" - installing zaproxy tool
		- output : if zaproxy says required Java 11
		- STEP 1.1 : `update-alternatives --config java` , output : if u don't see java 11 - then install it
		- Downloading + Installing Java 11 <br>1) search "openlogic JDK" OR [openlogic JDK downloads](https://www.openlogic.com/openjdk-downloads) <br>2) select options of each drop-down menu <br>3) download "11.0.21+9" `.deb` file <br>4) `cd Downloads` -> `dpkg -i openlogic-openjdk-11.0.21+9-linux-x64-deb.deb` <br>5) `update-alternatives --config java` -> select the no. - on which java 11 has
		- STEP 1.2 : run `zaproxy` , output : starts running <br>![[29_lecture-0-M3.jpg | 500]]
		- Note : don't choose any option & close the pop of "Do u want to persist the ZAP session" <br>- & it'll ask for updates - so u can update it later - cuz of time consume
	- STEP 2 : 2 types of Scan shown - so click on "Automated Scan" btn
		- output <br>![[29_lecture-1-M3.jpg | 500]]
		- in output , "URL to attack" input - wants a link on which u want to test
		- Advice : don't do any website like wscubetech - cuz this tool do a DOS attack ✔
		- STEP 2.1 : in "URL to attack" input , copy & paste the "http://testphp.vulnweb.com/"
		- in output , there's a "+" add button - which used to add tools , <br>- so we'll add tools - cuz till yet - we just gave a link , for support - need to add some tools ✔
		- STEP 2.2 : first add "Spider" -> then add "AJAX Spider"<br>- "Spider" : used to fetch all the pages links of that website <br>- "AJAX Spider" : will attack on those each pages (which is found by "Spider") of that website ✔
		- STEP 2.3 : click on "attack" btn , output : <br>![[29_lecture-2-M3.jpg | 500]]
		- STEP 2.4 : click "AJAX Spider" tab -> then click "Active Scan" tab , output : a progress btn will be shown <br>![[29_lecture-3-M3.jpg | 500]]
		- STEP 2.5 : click on that "Progress" btn , output : a Progress pop will get open <br>![[29_lecture-4-M3.jpg | 500]]
		- in output , those are attacks which are tried by Zaproxy tool ✔
		- STEP 2.6 : close the progress pop -> click "Spider" tab , <br>output : "spider" tab bringing all the pages of the website <br>![[29_lecture-5-M3.jpg | 500]]
		- in output of "spider" tab : green - means process is completed & red - means process is not completed <br>- & methods : GET , POST are being used to send & receive data ✔
		- STEP 2.7 : click "Alerts" tab - which used to show vulnerabilities of that website , output : <br>![[29_lecture-6-M3.jpg | 500]]
		- Q : in zaproxy tool , what confidence means in "alerts" tab ✔<br>Ans : [in zaproxy tool what confidence means in "alerts" tab](https://www.perplexity.ai/search/in-zaproxy-tool-voeZM60VR.672jqPe6RUvQ?s=u)
		- Q : in zaproxy tool , what risk means in "alerts" tab ✔<br>Ans : [in zaproxy tool what risk means in "alerts" tab](https://www.perplexity.ai/search/in-zaproxy-tool-voeZM60VR.672jqPe6RUvQ?s=u)
		- Q : in zaproxy tool - what Description , Other Info , Solution , Reference , Alert Tags means in "alerts" tab ✔<br>Ans : [in zaproxy tool - what Description , Other Info , Solution , Reference , Alert T...](https://www.perplexity.ai/search/in-zaproxy-tool-4.Rt8JbgQjiLsCWjV6_dlg?s=u)
		- in output : each vulnerability tab - will show particular URL - which has that vulnerability
	- once "Active Scan" Progress done 100% - then make the report on that website
	- STEP 3 : making a report on that website
		- STEP 3.1 : click on "Report" menu tab -> click "generate report"
		- u can change the "Report Directory" location - if u want <br>- cuz u don't need to follow STEP 3.3 - if u already put the file in desktop ✔
		- STEP 3.2 : click "Generate Report"
		- STEP 3.3 : open terminal -> `sudo su` -> go to "root" directory -> `thunar` -> copy the report <br>STEP 3.3.1 : paste it on Desktop - go to "Home/kali/Desktop"
		- STEP 3.4 : open it on Firefox
- STEPS : Practical Work - Website Attacks via Acunetix
	- download & installation - check 30th lecture

---
### Homework
1. 

---
### End of the lecture (Doubts) :
- Student Doubts
	- Q : Ghost framework for android - to get the remote access of a android device
		- Ans : in a terminal , a student giving an private IP of his phone
		- Doubt 1 : he's giving the IP to this tool - but not connecting remotely to this android phone ✔ <br>Ans : sir said - it'll take the IP , but it'll not connect - cuz android phone designed differently <br>- & a android phone made of different securities + it's made of linux & android = that's why - it's more secure ✔
		- Doubt 2 : can this tool hack - those android phones which are very old <br>Ans : sir said - might be & might not be - cuz a phone also has a firewall
	- Q : can a Wifi Tower possible to hack
		- Ans : No - cuz it's not easy to hack




