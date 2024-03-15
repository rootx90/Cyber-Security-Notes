#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : VPN & Proxy
> 1) Ways to be anonymous (from lecture 23)
> 2) About : VPN & Proxy
> 3) Practical Work of Manual Process : VPN
> 4) Practical Work of Manual Process : Proxy
> 5) Practical Work of Auto Process : Proxy
> 6) Hoisting a website in TOR

---
### Ways to be anonymous
> - for Changing user-agent + MAC address → go to 23th lecture
> 3. Changing IP address 
1. Changing IP address
	- 2 ways to change the IP address <br>1st way : Manual Process <br>2nd way : Auto/Automatic Process
	- in Manual Process , we use Proxychains (it's a in-built Proxy tool in kali)<br>in Auto Process , use VPN + Proxy ✔
### VPN & Proxy
- VPN
	- Virtual Private Network
	- How it Works ✔
		- our system has a Public Static IP address for surfing internet - Eg : 1.1.1.1 <br>now VPN (is a virtual system) - which has also a Public Static IP address , Eg : 2.2.2.2 & a open port - Eg : port no. 80
		- Q : what is virual/virtualization in terms of VPN ✔
			- Ans : not real , eg : Vmware <br>- Eg : in GTA game , whatever u're doing like u can (see + play + understand + etc) <br>all are virtual - but doesn't exist in reality
			- same way , VPN is a virtual system & we can use it - but in reality - it doesn't exist
		- so our system is connected with a VPN - & that VPN is connected with internet <br>- firstly , now our system searching "google" - then a request packet will be generated (from our system) <br>- so once a request packet gets generated - then our system will send the packet request via using it's own Public Static IP address <br>to that open port of VPN
		- - once that VPN got the packet request <br>Q : what VPN will do now ? <br>Ans : it'll stop the actual Public Static IP address of our system <br>- then VPN will send that packet request to the internet/www via using it's own Public Static IP address
		- Q : what's the security point here <br>Ans : in the process , the Public Static IP address of our system is not going to outside OR directly to the internet <br>- VPN will stop the Public Static IP address of our system from going to the internet <br>& VPN will use it's own Public Static IP address to access internet
		- now VPN will use it's own Public Static IP address - in order to send those request packets (of our system) to the internet <br>- now when the internet send response/reply - then the response will go to the IP address of VPN (not the IP address of our system) <br>- so internet response will go to 2.2.2.2 (which is a Public Static IP address of VPN) <br>- once that VPN system got the reply from the internet - then that VPN will send to our system's IP address
		- so here our system accessing internet indirectly - via VPN - in order to hide the Public Static IP address of our system <br>- so whatever work is happening - is done by VPN , our system & internet - not interacting each other directly ✔
		- hope u understood is : how our system's Public Static IP address is hidden & how the VPN works
- Proxy
	- How Proxy Works ✔
		- in Proxy , we have 2 real systems <br>our System has a Public Static IP address - Eg : 1.1.1.1 <br>& proxy System has a Public Static IP address - Eg : 2.2.2.2 & a open port
		- but the special thing about Proxy i.e a proxy has a list of many (Public Static IP addresses + ports) <br>- depends on how much that proxy required
		- so our system searched for google - due to search , a packet request will be created <br>- so our system will use it's own Public Static IP address (i.e 1.1.1.1) - to send the packet request to the "Proxy System"<br>- then "Proxy System" will use it's own Public Static IP address (i.e 2.2.2.2) - to send that packet request to the internet/www
		- Q : but how security comes b/w "Proxy system" & internet ✔ <br>Ans : this Proxy - has a list of (Public Static IP addresses + Ports) <br>Q : now first - what Proxy will do <br>Ans : "Proxy System" firstly send that packet request to the internet via using it's actual first Public Static IP address & a open port<br>- after sometime , once that first (IP address + that open port) time over , <br>then the "proxy System" will use the next IP address & a open port <br>- & so on that "Proxy System" will do switching from one (IP address + a open port) to another
		- so due to this , response & request of packets will go from one (IP address + a open port) to another of "Proxy System"
- Cons/weakness of VPN & why Proxy is better than a VPN
	- Q : why Proxy is better than a VPN <br>Ans : in a Proxy , there is a list of many both (Public Static IP addresses + open ports)
	- cons of a VPN : <br>- in a VPN , there's only one Public Static IP address & what if - this Public Static IP address is actual IP or fixed IP <br>- & jis kye liye VPN laye jana & lana kar rahaa hai <br>- if someone hack this IP then it'll will leak the actual Public Static IP address of that system
	- but in Proxy System , request & response of packets after transferring from switching (one IP address + a open port) to another <br>after certain period of time ✔
	- `imp Note ✅` : when the Proxy system do switching from one (IP address + a open port) to another <br>then that previously used (IP address + a port no) - will become no-active after a certain time <br>- so during switching - same thing happen with others (IP address + a port no) in Proxy system ✔
	- so in Proxy System , if someone try to trace/hack a IP address <br>- then if he/she traced the might be 1st IP - but that 1st IP will become disabled/no-active after a few time <br>- if the hacker also trace the 2nd IP - but then 2nd IP will become no-active after a few time ✔
- in Auto process , VPN is being used <br>& proxy is of 2 types : Manual Proxy (aka manual IP changing) & Auto Proxy

### Practical Work of Manual Process : VPN
- STEP 1 : download & install a VPN chrome extension <br>> VPN 1 : [Free VPN for Chrome - VPN Proxy VeePN](https://chromewebstore.google.com/detail/free-vpn-for-chrome-vpn-p/majdfhpaihoncoakbjgbdhglocklcgno) <br>> VPN 2 : [ZenMate-Best VPN for Chrome](https://chromewebstore.google.com/detail/free-vpn-zenmate-best-vpn/fdcgdnkidjaadafnichfpabhfomcebme) <br>> VPN 3 : Proton VPN
- STEP 2 : check ur Public Static IP address on [What Is My IP Address -IPv4 & IPv6](https://whatismyipaddress.com/) <br>- output : it'll show ur IPv4 + IPv6 + ur location (city + region + country) also <br>- so our details is leaking
- STEP 3 : turn ON the VPN & select a location - in order to get an IP address - then reload this website [What Is My IP Address -IPv4 & IPv6](https://whatismyipaddress.com/)
	- output : u'll get changed IPv4 & IPv6 + location will be shown (which u selected on VPN)
	- now that's fine - VPN saved our identity <br>Q : but how to know whether the VPN will leak our details or not ✔
	- STEP 3.1 : go to [DNS leak test](https://dnsleaktest.com/)
	- STEP 3.2 : in "DNS-leak-test" website , use both options i.e "Standard Test" & "Extended Test" <br>- output : that IP address will shown which is provided by VPN - via using both options <br>- `Note ✅` : if a different IP is shown in the website - then means VPN is leaking our details ✔
	- but it doesn't mean that VPN is not leaking our details - cuz we didn't seen yet - that how that VPN behind the scene is coded <br>- so never think that a tool is perfect
- `Note ✅` : the more we turn ON & OFF the VPN , then we'll get every time new Public Static IP address of VPN ✔

### Practical Work of Manual Process : Proxy
- Kali has it's own proxy by-default i.e "proxychains"
- STEP 1 : in order to run "proxychains" , we need do settings of it
	- Q : where is setting files located of any software in kali <br>Ans : /etc folder
	- STEP 1.1 : `sudo su`
	- STEP 1.2 : run `/etc` - then `ls` , output : proxychains4.conf - will be shown
	- STEP 1.3 : `gedit proxychains4.conf`
		- output : <br>![[24_lecture-0-M3.jpg | 500]]
		- in output , comment the "strict_chain" & comment out the "dynamic_chain" like this <br>![[24_lecture-1-M3.jpg | 500]]
		- "Strict_chain" : means it'll keep the Public Static IP address - remain fixed/static <br>"dynamic_chain" : keep the "Public Static IP address" - dynamic/changing <br>- so that's why , "dynamic_chain" required ✔
	- STEP 1.4 : inside "proxychains4.conf"
		- scroll down - u'll see an example of proxylist<br>![[24_lecture-2-M3.jpg | 500]]
		- "socks4" : is also a protocol which used for data transfer for only proxies ✔
		- Note : if username & password in any IP then it's fine <br>but generally IP don't contain username & password
- now we need to add IPs inside the proxychains , we can't put any list of IPs in proxychains <br>so we'll get list of IPs for proxies from browser
- STEP 2 : in firefox , search "free proxy list"
	- output : 
		- in https://free-proxy-list.net , contains IP , Port no. - but it doesn't have Protocol <br>- so this website is not useful
		- in https://geonode.com/free-proxy-list , contains IP , port , protocol
	- STEP 2.1 : from [Free Proxy List](https://geonode.com/free-proxy-list) , copy IP + port no. + protocol
		- inside "proxychains4.conf" file , after "# defaults set to "tor"" line - paste around 30 each proxies according to sequence<br>- means 1st Protocol comes - then IP - then port no.
		- output : <br>![[24_lecture-3-M3.jpg | 300]]
	- STEP 2.2 : save the file
- STEP 3 : take any website URL - Eg : `file://usr/share/kali-defaults/web/homepage.html`
	- STEP 3.1 : in terminal , run `proxychains wget file://usr/share/kali-defaults/web/homepage.html` <br>- "wget" : means to download stuff from the website ✔<br>- output :<br>![[24_lecture-4-M3.jpg | 500]] <br>- in output , this error means u copied the wrong IP
	- STEP 3.2 : run `proxychains wget https://testphp.vulnweb.com/login.php`<br>- output : one by one IP will get changed once that IP's gets timeout <br>![[24_lecture-5-M3.jpg | 600]]
	- Experiment 1 : come out from root folder cuz browsers doesn't work on root ,  run `proxychains firefox` <br>output : will not work <br>Experiment 2 : same output error comes in chrome - after running `proxychains chrome`
- Q : whatever we did via manual Process of Proxy , what's the cons/weakness ✔
	- Ans : in manual process of Proxy , we used list of IPs from a website <br>& what if that IPs already hacked by a hacker OR that hacker made the website for us as a trap
	- so manual proxy is not good way , that's why - use Auto process of proxy i.e TOR browser

### Practical Work of Auto Process : Proxy
- Q : Auto Process vs manual process for proxy - which is better ✔
	- Auto Process cuz in manual process we need give manually <br>many IP-addresses & port no. for each IP-addresses 
	- & for long term , manual process is not effective
	- Manual Process of Proxy - was just an example - in order to understand why we need Auto Process
- STEPS - TOR browser : Download , Install & use
	- STEP 1 : download & install TOR browser for Linux - [Tor Project | Download](https://www.torproject.org/download/)
	- STEP 2 : in kali , go to "Downloads" folder & extract it - then open "tor-browser" folder
	- STEP 3 : double click on "start-tor-browser.desktop" - then click "launch-anyway"
	- STEP 4 : click on "connect" button , output : now connection will starts & chains of different proxies is started
		- STEP 4.1 : in tor browser , search "wscubetech"
		- Q : why we use TOR browser OR Security of TOR browser<br>Ans : we'll get the 3 Circuit - i.e <br>![[24_lecture-6-M3.jpg | 500]]
		- each of those 3 Circuits are in different location
		- 1st Circuit : Guard - means most secured & more configured & after all those 3 IPs <br>- then the server comes of TOR browser ✔
- STEPS - TOR tool : download , install & use
	- there's a terminal tool just like TOR browser i.e "tor" <br>it converts a system into a complete circuit ✔
	- STEP 1 : to install , run `sudo apt install tor`
	- close the TOR browser - otherwise issues will come during applying circuit
	- STEP 2 : & run `tor` , output : now circuit will be started to apply to our system
	- once 100% done - means applying a circuit in a system is completed ✔
	- STEP 3 : install it in Chrome/firefox browser : [Onion Browser Button - by benthum](https://chromewebstore.google.com/detail/onion-browser-button/fockhhgebmfjljjmjhbdgibcmofjbpca)
		- Note : if 100% circuit is not done then this extension will not work <br>when 100% circuit is completed - then only the extension will work ✔
		- pic ![[24_lecture-7-M3.jpg | 400]]
		- in pic , "Onion-browser-button" extension has 2 buttons <br>1st : gray button - is to disable <br>2nd : purple button - is to turn ON
		- STEP 3.1 : click on "purple onion" button - to start the proxy connection , output : connected with any first IP + a port no<br>![[24_lecture-8-M3.jpg | 400]]
	- STEP 3.2 : Now check IP on [What Is My IP Address - See ur Public Address - IPv4 & IPv6](https://whatismyipaddress.com/) , output : u'll get different (IP + location) <br>- Note : if this website - shows location "India" - then means it's leaking our details
	- STEP 4 : disable the "Onion Browser Button" extension
- we can also host our website not directly in Dark Web - but in TOR ✔

### Hoisting a website in TOR
- Q : what we have right now - so that we can bring it Online <br>Ans : i.e Apache pages - which we earlier saw
- STEP 1 : `sudo su`
- STEP 2 : run `service apache2 start`
	- Q : on which port no. - localhost goes online ✔<br>Ans : port no. 80
	- STEP 2.1 : open a browser & write on address bar - `localhost:80` , output : Apache2 page will come 
	- we want to host this website in TOR - for it , we need to do configuration in "TOR" folder
	- Q : which folder contains configuration files of all softwares <br>Ans : `/etc`
	- STEP 2.2 : run `/etc/tor` - then ls , output : torrc file 
	- STEP 2.3 : run `gedit torrc` , output <br>![[24_lecture-9-M3.jpg | 500]]
	- in output , uncomment those 2 marked lines
		- "HiddenServiceDir /var/lib/tor/hidden_service/" : <br>means TOR will give a link on this path - in order to access that Hosted website ✔
		- & "HiddenServicePort 80 127.0.0.1:80" : <br>means TOR will get this (by-default IP with port no. 80) online ✔
- STEP 3 : run `tor`
- STEP 4 : in terminal , go to this location `/var/lib/tor/hidden_service/` - then `ls` , output : a "hostname" file will be shown
	- STEP 4.1 : run `cat hostname` , output : a onion link will be shown
	- Q : which link is this ✔<br>Ans : i.e Tor - mean it's a link of that website
	- `Note ✅` : u can access "onion" link only via TOR browser , not via normal browsers
	- STEP 4.2 : open Tor browser -> click on "connect" button & paste the link , output : the Apache2 page will be shown <br>![[24_lecture-10-M3.jpg | 500]]
	- so we're able to use the "Apache2 page" as a website
	- u can also put "IP & port no." of ur website in "HiddenServicePort" link - then our actual website also be hosted in TOR ✔ <br>& that onion link of our website can be shareable to anyone (who use TOR)
- `Note ✅` : the more u turn OFF & ON the tor - then every time u'll get a new onion link  - u can't access the content via pervious link ✔

---
### Homework
1. 

---
### End of the lecture (Doubts) :
- Q : why not to use Manual Process to hide/change our IP address 
	- Advice : hide/changing  IP address via Manual Process - is just an example ✔
	- but not useful - using Manual Process to hide IP address
	- & even our own details were getting leaked via manual process
- Q : how to make a file or folder online via apache2 service ✔
	- in Kali
		- STEP 1 : `sudo su`
		- STEP 2 : run `service apache2 start`
		- STEP 3 : go to this location , run `/var/www`
		- STEP 4 : `ls` - then `cd html`
		- now inside "html" folder make a folder - Eg : "test"
		- STEP 5 : run `mkdir test` - then make 3 folders inside "test" folder
		- STEP 6 : open browser , run `localhost:80`
		- STEP 7 : now in address bar , run `localhost/test` , output : u'll able to see + access those directories in browser
		- so these are steps to bring a file or folder online
	- STEP 8 : in VMware , if u installed a ParrotOS OR any OS - then open it
		- STEP 8.1 : in Parrot OS , open a browser
		- STEP 8.2 : in a browser , write the IPv4 of Kali OS then port no. <br>Eg : `192.168.186.143:80` , output : apache2 page will be accessible
		- STEP 8.3 : accessing that folder , write in address bar - `http://192.168.186.143/test/` , output : directories also accessible
		- we did local machine to local machine to send (the small KB size downloadable files) 
		- but u can use this way to send world-wide <br>- to send world-wide , we need a public static IP address - which we can get cloudflared tool
- Q : imsi vs imei vs IP-address ✔
	- imsi no. : is used for identity , system can't be hacked via IMSI <br>cuz no network is created via IMSI
	- u can only hack stuff via that thing - which uses internet i.e IP-address , bluetooth (also create a network)
	- IMEI no. - is a identity of a phone & not changeable but MAC-address can be changed <br>- in order to change IMEI no. - then we need change the hardware ✔
	- so when u purchase a SIM for the phone (which contain IMEI no.) <br>- so ISP (of that SIM) will get the details of both SIM + IMEI no. of ur phone <br>- when we give IMEI no. (of that phone) to Police - then Police will give that IMEI no. to that ISP ✔ <br>- then ISP checks which SIM is attached with that IMEI no. <br>- once ISP got to know about IMEI no. has that SIM - then that SIM is also linked with Aadhar Card of the user <br>- then ISP give details of Aadhar Card (of the user) to the Police
	- when Phone gets stolen - then thief shut-down the phone <br>- so once that Thief insert a SIM to that IMEI no. - then all ISPs got the details <br>- cuz once the Theif insert a SIM then IMEI no. details go to ISPs
	- Q : what if that thief didn't insert a SIM - then what'll happen <br>Ans : then WIFI ISP will get the details <br>![[24_lecture-11-M3.jpg | 500]]
	- via IMEI no. - phone cloning also happen <br> so IMI phones has same IMEI no. - that's why police not able to find thief
	- Hackers use someone's SIM to call a Victim - but they don't use their own actual SIM
- Q : is IP will get change/bounce in our SIM - just like proxy ✔
	- Ans : if u purchase VPN , Proxy - then our details will get leaked & u can't hide
	- so never do any illegal work - which requires to hide the IP-address <br>& those who do - then they use someone's wifi - to do illegal activities
- Q : MAC address can't give more details about Victim, except details about company of that MAC-address
- Advice : always keep ur wifi password strong
- Mine Doubts
	- for more about Practical Manual Process of Proxy i.e "proxychains" : <br>[Installing Tor services on Kali Linux & usage of Proxychains. practical lab lecture 4 - YouTube](https://www.youtube.com/watch?v=6vg5JlQhHgo&ab_channel=NetworkingRoot)
	- Q : diff b/w TOR tool & TOR browser
		- TOR tool : 
			- aka Tor (The Onion Router)
			- is a network that anonymizes web traffic to provide private web browsing. <br>It is a communication protocol that uses a network of relays to hide a user's IP address and location, <br>making it less known about the user than conventional browsing methods
		- TOR browser : 
			- is a web browser that comes equipped with Tor and other anonymizer tools. 
			- It is designed to allow users to browse the web with more anonymity. 
			- it hides the user's IP address and browsing activity by redirecting web traffic through a series of different routers known as nodes

