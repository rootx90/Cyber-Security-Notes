#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : Vulnerability Assessment by Acunetix Pro & Wi-fi Hacking
> 1) Download & installation : Acunetix tool
> 2) Practical Work : Vulnerability Assessment via Acunetix tool
> 3) Concept : Wifi-hacking
> 4) Buying Suggestions : USB wifi-adapter
> 6) Practical Work : wifi-hacking via a USB wifi-adapter device

---
### Download & installation : Acunetix tool
- STEP 1 : search "Acunetix crack github" OR [How to install acunetix (linux) · GitHub](https://gist.github.com/Ademking/fbc6977b555d930224b291bb26e44f2e)
- STEP 2 : click on mega link
- put the downloaded files in Desktop
- STEP 3 : `sudo su` -> `cd Desktop` -> `unzip AWVS\ 13.x-20230428T234029Z-001.zip` , output : "AWVS 13.x" folder
- STEP 4 : `cd AWVS\ 13.x`
- STEP 5 : Now run further commands from that github gist
	- STEP 5.1 : `chmod +x acunetix_13.0.200217097_x64_.sh`
	- STEP 5.2 : `./acunetix_13.0.200217097_x64_.sh` -> then hit "enter key" -> then "q key" -> press "yes" to accept the license <br>-> give default hostname "kali" -> give a random email address "`<name>@gmail.com`" -> give a password "name@123"
	- Output : Extracting files <br>Note : don't forgot the email + pass = so note them down in a txt file<br>- Now till yet , we just installed it - now run further commands to crack it ✔
	- STEP 5.3 : before running this command - `cp Crack/wvsc /home/acunetix/.acunetix/v_200217097/scanner/`
		- STEP 5.3.1 : `cd AWVS\ 13.x` -> ls , output : u'll not see any "Crack" folder - but "wvsc" folder exists
		- Q : what we'll do now ✔<br>Ans : remove the Crack folder from the command
		- STEP 5.3.2 : run `cp wvsc /home/acunetix/.acunetix/v_200217097/scanner/` -> hit enter , <br>output : no errors will be shown - which means command is executed properly
	- STEP 5.4 : in next command - remove the "Crack" folder , run `cp license_info.json /home/acunetix/.acunetix/data/license/`
	- STEP 5.5 : run `systemctl start acunetix.service` - now starting the service of this tool , <br>- "systemctl" : means run services of this tool in background ✔

### Practical Work : Vulnerability Assessment via Acunetix tool
- during installation - we got a link "`https://kali:3443`" <br>![[30_lecture-0-M3.jpg | 500]]
- STEP 1 : copy the link "`https://kali:3443`"  -> open firefox
	- STEP 1.1 : paste the link , output : a warning will be shown 
	- STEP 1.2 : click on "advanced" btn -> "accept the risk & continue" btn , output : <br>![[30_lecture-1-M3.jpg | 400]]
	- STEP 1.3 : write the email & pass which u made - during installation of it -> check the checkbox "keep me signed in" -> click Login
	- STEP 1.4 : click on "Add a Target" link , output : define the victim's address - on which u want to do scanning/testing
	- STEP 1.5 : copy "http://testphp.vulnweb.com" -> paste on "address" input -> add description as "test/testing" , output <br>![[30_lecture-2-M3.jpg | 500]]
	- STEP 1.6 : click on "Save" btn , output : now finally the target is added for scanning/testing
- STEP 2 : select scan speed "moderate" - cuz fast scan = most of the stuff skipped from scanning
	- in "Site login" , give username & password - Cuz <br>Eg : two people are testing the "Amazon" website ✔<br>1st person doing without login & 2nd person doing with login <br>Q : which person will get more information ✔<br>Ans : 2nd person - cuz 2nd person doing scanning after login
	- STEP 2.1 :  in "site login" section , write username & password as "test" -> click ("Save" btn -> then "scan" btn) <br>STEP 2.1.1 : select "report" as Developer , "Schedule" as Instant -> click "create" scan
	- output error : the target was not responsive - means kali's network is not connected <br>Solution of output error : connect ur kali's network properly - then run the scan
	- STEP 2.2 : once u report is generated , click "Generate Report" btn -> select "developer"

### Concept : Wifi-hacking
- Note : a wifi adapter required to do wifi-hacking - we'll see in practical
- understanding Concept : working process & communication b/w devices & the wifi-router ✔
	- u have a router & a device (eg : laptop/phone/PC)
	- Q : first step - what u'll do in order to connect with ur router device ✔<br>Ans : <br>1st : u'll check the wifi name <br>2nd : u'll click on that wifi name<br>3rd : give password <br>4th : click on "Connect" btn
	- after when u clicked on "Connect" btn - then a packet will be generated <br>(which contain password + MAC address of our device Eg : lapi)<br>- Note : without generating the packet , password can't go from our device to the router ✔
	- so that packet will go from ur device to the router - now the router will check whether that password is correct or not <br>- Assume , ur wifi password is correct & the router is connected with ur device <br>- so once ur device connected with the router - then the router also get the MAC address of that connected device
	- Till yet , it's a basic working b/w ur device & the router
	- in this basic working , the packet (which is sent from ur device to the router - for checking password whether is it correct or not) <br>- that packet aka "**handshake file**" <br>Q : why that packet aka "**handshake file**" <br>Ans : cuz when a 1st time , a new connection/communication going to establish b/w two devices = then <br>aka a handshake file created (i.e handshake packet file) b/w those 2 devices
	- now Q : what identities the router have <br>Ans : <br>1) IPs <br>2) its MAC address <br>3) Q : what is 3rd one - mean how do u identify ur wifi - Ans : name of the router 
	- acc. to router's terminology : <br>- name of the router = aka ESSID <br>- MAC add. of the router = aka BSSID
		- Note : to remember this term <br>Q : out of these two , which one u can edit acc. to u <br>Ans : i.e name , so assume that in "ESSID" - "E" means edit
	- assume that router's name = wscubetech
- till yet , we just understood working b/w the device & the router <br>Now let's see what're vulnerabilities - due to which the router or wifi-hacking possible
- Understanding Concept : how wifi-hacking possible ✔
	- 1st vulnerability : ✔
		- at 1st time - when u shared/wrote the password (of the router) via our device (eg : phone/lapi/PC) <br>- then obviously, that password is saved in that device - cuz Eg : due to that saved password in that device, <br>when u come in range of that router's signal - then automatically ur device quickly send the "handshake file" to the router 
		- so that "handshake file" contain the router's password 
		- conclusion :
			- every time - ur device come in range of wifi-router's network <br>- then ur device will send the "handshake file" again & again to the wifi-router
			- means the more ur device coming in range of a wifi-router <br>- then ur device sending the "handshake file" again & again to the wifi-router
	- 2nd vulnerability : ✔
		- we assumed that our wifi-router's name is wscubetech
		- Situation : now let's say - ur going outside to the coffee shop <br>- Note : if anything is different in ESSID/name of that unknow router <br>then ur device will not send "handshake file" to that unknown router <br>Q : But what if ur device got the exact same ESSID/name of that unknown router - then what ur device (eg : phone) will do ✔<br>Ans : means both ur home wifi router's name & that unknown router's name = wscubetech = means both have same ESSID <br>- so ur device will send a "handshake file" again & again - to that unknown router <br>so that ur device able to establish connection with that unknown router
		- so ur device (eg : phone) has a vulnerability <br>- means ur device is make connection with that unknown router - based on the name/ESSID ✔ <br>- so ur device will send the "handshake file" to the unknown router - doesn't matter even the password is wrong ✔
	- Q : as a attacker , what u do ✔<br>Ans : we (as a attacker) - we need that packet
		- Q : How 2nd vulnerability consider as a vulnerability ✔<br>Ans : let's say 2 persons & both person has a exact same name = Rakesh <br>- Assume , u took the money (for an emergency) from 1st Rakesh - but u returned the money to 2nd Rakesh <br>- so this is a vulnerability - that u didn't identify the face of 2nd Rakesh <br>so due to this situation , 2nd Rakesh taking advantage of having "exact same name"
		- Eg : ur device sending a "handshake file" (as a packet - which contain router's password + MAC address of ur device) <br>to the that unknown wifi-router ()<br>- & what if behind-the-scene , that unknown router (which has a same name = our home's wifi-rotuer) is of a hacker <br>- then that hacker will take away the "handshake file"
		- so same - we (as a attacker) capture that packet (aka "handshake file") <br>Q : how do we capture that packet/handshake-file <br>Ans : see in Practical work
	- earlier , wifi-router's get the password packet in text form - means easy to see <br>- then WPA security came - but WAP security can be easily cracked <br>- then WPA2 security came - but it's not easy to crack ✔
	- Practical Theory : Q : how to capture that packet ✔
		- Ans : a hacker/attacker has a wifi-adapter <br>- & wifi-adapter is also in ur system (which is capturing wifi - means it's running ur wifi) <br>- but normal people who use wifi-adapter is different - than hacker/attacker's wifi adapter ✔
		- in a hacker/attacker's external wifi-adapter , that hacker/attacker connects on his/her own system <br>- that external wifi-adapter has 2 mods ✔<br>1) Managed mode : does only normal work like connecting wifi & providing network <br>2) Monitor mode
		- about "Monitor Mode" : means which just see what things going on
			- Eg of Monitor Mode : in school , there's a monitor - that keeps an eye on each student <br>so Monitor Mode - doesn't provide net , it only monitors those networks - which are in range of it ✔
			- Q : out of these 2 mods , which one is by-default same as wifi-adpapter used by normal users  ✔<br>Ans : i.e manage - cuz that wifi-adapter does only normal work <br>- & hacker/attacker's wifi-adapter has both powers (manage + monitor)
			- so it'll monitor all the networks which comes in its network range
		- so the wifi-adapter (of hacker/attacker) capture/take the packet - without connecting on victim's (device & wifi-router) ✔
		- Q : de-authentication vs authentication ✔ <br>Ans : <br>authentication : <br>- means the device (eg : phone) already authenticated with the another device (eg : wifi-router) <br>- means the phone is already legal/valid device for that wifi-router , so the phone is not unknown for that wifi-router<br>de-authentication : <br>- means de-authenticate the phone which is already authenticated with that wifi-router <br>- so de-authentication = will make that phone unknown/invalid/illegal for that wifi-router <br>due to which , the phone needs to connect again with that unknown wifi-router
		- so we (as a hacker/attacker) - select the Victim's wifi - then we send a de-authentication packet <br>- currently a Victim's device is connected properly with the his own wifi-router <br>- Now consider urself as a router & u switched ur wifi-adapter's mode into "monitor-mode" <br>then u attacked & send a de-authentication packet on Victim's device - then that wifi-router will disconnect that Victim's phone
		- Q : now once the device is de-authenticated - then what the device will do <br>Ans : the device will reconnect - & due to reconnecting , the device will send the packet (aka "handshake file") to the wifi-router <br>- so here , we (as a attacker) already ON the Monitor mode (of wifi-adapter) <br>- so via that "Monitor Mode" , we'll capture that packet <br>- & once we got the packet - then we'll stop (sending the de-authentication packet + connection) to the Victim's device<br>- & once we stop the our connection - then again Victim's device send the packet to connect on his wifi-router
		- Doubt of students : <br>Q : do we (as a attacker) need to disconnect that Victim from his device from the his wifi-router <br>Ans : yes , if that device not used by any victim - then we'll wait for a victim to use that device<br>- Note : if we send many de-authentication packets on Victim's device <br>- then his device not able to connect to our wifi-adapter aka "DOS in WIFI" ✔ <br>Q : can we do this practical to that device which is connected with LAN cable wifi ✔<br>Ans : No , cuz we need wireless wifi <br>Q : is this practical can be down via our device's wifi-hotspot - which acts a router <br>Ans : yes
- Conclusion Pic : <br>![[30_lecture-3-M3.jpg | 600]]
- Q : do u know on what basis - wifi works ✔
	- Ans : wifi works on frequencies
	- Eg : if u heard about "radio 98.3 fm" , 93.5 , etc <br>here 98.3 , 93.5 , etc = aka frequencies ✔
	- Assume 98.3 to 100 or 93.5 to 95 , so the range "from 98.3 to 100" considered as a group of channels/frequencies <br>- so many frequencies comes inside b/w "98.3 - 100" ✔
	- so range could be b/w any frequency , <br>- so when many no. of frequencies create a range = aka channels 
	- so wifi works on the basis of those channels ✔
	- conclusion Pic : <br>![[30_lecture-4-M3.jpg | 300]]
	- for more : <br>- [On what basis wifi works Give me short points in bullet](https://www.perplexity.ai/search/On-what-basis-vu1wXilqQpK4lrqulZa9Xg?s=u) <br>- [That's How Wi-Fi Works - YouTube](https://www.youtube.com/watch?v=hePLDVbULZc)

### Buying Suggestions : USB wifi-adapter
- sir using : TP-Link TL-WN722N V4 : [TL-WN722N | 150Mbps High Gain Wireless USB Adapter | TP-Link India](https://www.tp-link.com/in/home-networking/adapter/tl-wn722n/v4/)
- Buying Guide Advice : ✔<br>1) that USB wifi-adapter should be linux supported <br>2) Monitor Mode supported <br>Note : if Monitor Mode is not supported - but Linux Supported - then that's also fine to buy ✔ <br>3) only take branded companies : <br>Note : cuz unknown brand's wifi-adapter doesn't support drivers or u might not get drivers online for those wifi-adapater <br>- only buy branded companies : cuz u'll get drivers easily
- Q : recommended wifi-adapters - instead of TP-Llink TL ✔<br>Ans : check description of this vid : [Kali Linux TP-Link TL-WN722N install (1 command fix) - YouTube](https://www.youtube.com/watch?v=-xkpgvjuEy0&ab_channel=DavidBombal) <br>> [Best WiFi Hacking Adapters in 2021 (Kali Linux / Parrot OS) - YouTube](https://www.youtube.com/watch?v=5MOsY3VNLK8&ab_channel=DavidBombal)
- Note : before doing wifi-hacking practical with any wifi-adapter , 1st download it's driver for kali linux
### Practical Work : wifi-hacking via a USB wifi-adapter device
- STEP 0 : in kali , `sudo su`
- STEP 1 : plugin that USB wifi-adapter 
- STEP 2 : how to select that device - in order to make it connected with Kali OS 
	- For Virtual Machine , click on that wifi-adapter to connect <br>![[30_lecture-5-M3.jpg | 500]]
	- For Vmware , click on "Connect"<br>![[30_lecture-6-M3.jpg | 500]]
- STEP 3 : Q : to check whether that connected or not
	- 1st way to check it : <br>Ans : in Kali , top right corner -> hover on wifi -> u'll see more networks in "Available Networks" <br>![[30_lecture-7-M3.jpg | 500]]
	- in output , if "available Networks" showing - then means that wifi-adapter is connected
	- STEP 3.1 : run `ifconfig`<br>2nd way to check it whether it's connected or not : i.e `ifconfig` <br>- cuz this device comes under "ifconfig" - that's why "ifconfig" will show it ✔<br>![[30_lecture-8-M3.jpg | 500]]
	- in output , ✔<br>- one "lo" coming : means one localhost is connected <br>- eth0 : means ethernet <br>- one "wlan0" showing : means a wifi-adapter is connected/plugin
	- so "ifconfig" will operate that device , operate - means both ON/OFF ✔ <br>- if u wanted to do changes in that "wlan0" device - like switching mode of that device into monitor mode , etc <br>then use "`iwconfig`"✔
	- by-default a wifi-adapter will be in "Manage mode" , <br>to change the mode into Monitor mode - run "`iwconfig`" command ✔
	- STEP 3.2 : run `iwconfig` , output : <br>![[30_lecture-9-M3.jpg | 500]]
	- in output , see the "Mode" = managed <br>- to see details of connected wired devices - use "`iwconfig`" ✔ <br>- so if u run "`ifconfig`" = then u'll not see any "mode" shown in that device <br>cuz "ifconfig" only showing that device is now connected ✔
	- Conclusion : ifconfig vs iwconfig ✔<br>- "ifconfig" command : use for only turn ON/OFF that connected device <br>- "iwconfig" command : use for only changing the mode or changing a setting of that connected device
- STEP 4 : changing "managed" mode into "monitor" of that wifi-adapter
	- Q : what 1st thing - we need to do to change the mode into "Monitor" mode of wifi-adapter ✔<br>Ans : we need to shut down this wifi-adapter
	- to shut-down/OFF any network device , syntax `ifconfig <network-interface-name>` <br>- interface : means name of the network - Eg : eth0 , wlan0 , etc ✔
	- STEP 4.1 : run `ifconfig wlan0 down` , output : now "`eth0`" interface (means that wifi-adapter) is closed 
	- Q : to change the device - in "monitor" mode - then which command ifconfig OR iwconfig <br>Ans : iwconfig
	- STEP 4.2 : run `iwconfig wlan0 mode monitor`
	- STEP 4.3 : Q : now turn ON that device - which command used ifconfig OR iwconfig <br>Ans : ifconfig <br>- run `ifconfig wlan0 up`
	- STEP 4.4 : to check whether the mode has been changed or not , run `iwconfig` , <br>output : has been switched into "Monitor mode" of wlan0 interface
	- `Note ✅` : right now we switched it into "Monitor Mode" ✔
		- but in Kali OS , there are many applications/devices - which need network most of the time
		- so we changed it into "monitor Mode" - but "Monitor Mode" doesn't provide network <br>- due to this - in this situation , when those applications/devices need network <br>Q : then what those applications/devices will do - to get the net <br>Ans : those apps/devices will change that mode into default mode i.e "managed mode" <br>- cuz any application/device which required to connect with net/internet - then that app/device will automatically gets connected <br>- Eg : if u disconnect that device/app - then when u bring that app/device in network's range - then it'll automatically connect <br>- same here , when that device/app need net - then firstly that app/device will go to that thing (which provide net) <br>so net is provided by "Managed Mode" - that's why - that app/device will keep switched into "managed mode" 
	- that's why - due to this issue , we need to run a command <br>- `Note ✅` : due to this command , network connection will get disconnected of each applications <br>means no devices/apps can't use network ✔
	- STEP 4.5 : in kali OS , top right corner , hover on network icon , output : net is connected right now
	- STEP 4.5 : running a command to stop from switching into "Managed Mode" <br>- run `airmon-ng check kill` , output : <br>![[30_lecture-10-M3.jpg | 300]]
	- tools used for wifi-hacking ✔<br>1) airmon-ng : used only to disconnect/close network services - which is running in TaskManager <br>& due to this , those devices./apps (who are using network) not able to run - then those apps/devices can't able <br>change the mode into "Managed Mode"<br>eg : `airmon-ng check kill` - means whatever devices/apps using internet - check them all - then kill them after checking <br>2) aireplay-ng : used send a de-authentication packet <br>3) airodump-ng : used to monitor all those networks (that are near to the wifi-adapter) + select a victim target + capture the handshake file <br>4) aircrack-ng : used for password cracking
	- till yet , we disconnected all those devices/apps which were using network
	- `Advice ✅` : once that USB wifi-adapter connected to the Kali OS system <br>- then always run 1st command is "`airmon-ng check kill`" -> <br>then run "ifconfig wlan0 down" -> then "iwconfig wlan0 mode monitor" -> then "ifconfig wlan0 up" ✔ <br>![[30_lecture-11-M3.jpg | 300]]
- STEP 5 : run `airodump-ng wlan0`
	- in command , Q : via which thing - the airodump-ng will monitor all other networks - which are in range <br>Ans : "wlan0" - cuz it's a wifi-adapter <br>- conclusion : airodump-ng will monitor all other networks (which are in range) via "wlan0" ✔
	- output : <br>![[30_lecture-12-M3.jpg | 400]]<br>- in output , it's scanning channels
	- STEP 5.1 : Note ✅ : if channels are not showing - then disconnect & reconnect that USB wifi-adapter
		- then again run `airodump-ng wlan0` , output : <br>![[30_lecture-13-M3.jpg | 500]]
		- in output , ✔
			1. CH : means channels , Eg : see the "CH" column , different wifi-networks on a different channel no. <br>- Note : Q : some wifi-networks have same channel no. 5 <br>Ans : cuz those wifi-networks are a operated/running via a single router -  means both router is a same <br>- that's why , those have same channel no. - only difference is person kept different names i.e ESSID<br>- those network - whose have same channel no. - then means - might be that person created 2 different wifi <br>like one for 4G & another for 5G OR might that person created 2 different network in 4G ✔<br>- Conclusion : if those network - whose has a same channel no. = means wifi-router is same ✔
			2. BSSID : <br>Q : what was the BSSID <br>Ans : MAC address <br>Q : MAC address of whom <br>Ans : of router
			3. PWR : aka power <br>- means which wifi-networks are closer to u & far from u <br>Eg : "-92" - means very far from ur network , "-28" is closer to ur network <br>- means a more negative no. = far & a less negative no. = closer <br>- PWR : just tell that whether that wifi-network is in ur network's range or not ✔
			4. Beacons : it's not useful for us
			5. `#data` : means how much data getting share
			6. MB : means showing the speed of each network
			7. ENC , CIPHER , AUTH : all 3 related to wifi-security <br>- ENC : eg - WAP2 : here version 2 of WPA used <br>- CCMP : we'll learn in cryptography , eg : CCMP - means is a type of encryption - used for those each network<br>- AUTH : means authentication , eg : PSK - public security key - means a public security key used in those each network <br>means the password that u wrote - to connect with ur mobile wifi
	- Note : don't do this in ur network - cuz u'll get disconnected from ur own wifi-network
	- STEP 5.2 : close the process , press `CTRL + C`
	- now let's choose a targeted wifi
		- Eg : `airodump-ng wlan0 --bssid 8C:A3:99:F8:14:99 --channel 11 --write HARSH`
		- in this command , <br>1) "airodump-ng wlan0" : airodump-ng will select the target via wlan0 interface (i.e USB wifi-adapater) <br>2) "--bssid 8C:A3:99:F8:14:99" : selected the MAC address of a targeted Victim's wifi-router <br>3) "--channel 11" :  wrote the channel no. - on which that targeted router's MAC address showing <br>`to understand easily ✅` : <br>- assume that MAC address is working as a IP <br>- & the channel no. (of that MAC add.) is working as a portno.<br>4) "--write HARSH" : <br>"`--write`" - means capturing/fetching the handshake file & saving it in a HARSH file<br>& HARSH - we gave a file name as HARSH - which contain info of Victim's handshake file
		- Conclusion Pic : <br>![[30_lecture-14-M3.jpg | 500]]
	- channel no. vs port no. : ✔
		- Q : what is a channel no. <br>Ans : a channel no. works like a port no. <br>Eg : earlier when u want to listen radio - then we turn the button either left or right - in order get that frequency
		- Q : Why means we kept that button on that frequency <br>Ans : cuz that radio signals transmitting the data on that frequency only like 98.3 , etc <br>- Eg : in networking , <br>Q : why only in port no. 21 = FTP runs <br>Ans : cuz FTP sends the data only on portno. 21 <br>- same with SMTP send it's all data only on port no. 25 <br>- HTTP sends it's all data only on port no. 80
		- for wifi , portno. concept doesn't come ✔<br>- each wifi has different channel no. - instead of port no. <br>Eg : each wifi-router network working on a different channel no. <br>& those wifi-router network has same channel no. = means both wifi-router networks working on same frequencies/channels 
- further steps done in - 31th lecture


---
### Homework
1. 

---
### End of the lecture (Doubts) :
- commands to install drivers for TP-Link wifi adapter
	- STEP 1 : `apt install dkms`
	- STEP 2 : `apt install realtek-rtl88xxau-dkms`
- Q : in wifi-hacking , 2 things done to complete the process of wifi-hacking ✔<br>1) wifi-scanning <br>2) password cracking
- Q : related to router 
	- Q 1: when a first connection establish between the laptop & the router <br>- is that router will take the laptop's MAC address ✔<br>Q 1.1 : nce connection process is completed & the router is completely connected with the device like laptop <br>- then will the router keep the laptop's MAC address to remember ✔<br>Q 2 : how does a router remember the mac address of a connected device ✔
	- Ans 1 & 1.1 : Once the connection process is completed and the router is completely connected with the device like a laptop, <br>the router does not keep the laptop's MAC address to remember. <br>The MAC address is a unique identifier for each network interface in a device, and it is used to identify devices on a network. <br>When a device connects to a network, the router does not automatically assign its MAC address to the connecting device. <br>Instead, the router uses the MAC address of the connecting device to communicate with it during the connection process.
	- Ans 2 : A router remembers the MAC address of a connected device through the Address Resolution Protocol (ARP) cache. <br>When a device connects to a network, the router sends a broadcast ARP message to ask for the MAC address of the device. <br>The device responds with its MAC address, and the router stores the IP to MAC address relation in its ARP cache <br>for use at a later time. The router identifies devices by their physical address, known as the MAC address, which is unique
	- complete Answers link : [router's related doubts](https://www.perplexity.ai/search/when-a-first-d5phkurDTrSYX5LZVjEfNA?s=c) <br>Q 3 : [networking - How does my router identify different devices? - Super User](https://superuser.com/questions/807576/how-does-my-router-identify-different-devices) <br>Q 4 : [Do routers save MAC addresses for devices that were once on the network? Or only MAC addresses for devices currently on the network? - Quora](https://www.quora.com/Do-routers-save-MAC-addresses-for-devices-that-were-once-on-the-network-Or-only-MAC-addresses-for-devices-currently-on-the-network) <br>Q 5 : [What is the use of a MAC address in a router? - Quora](https://www.quora.com/What-is-the-use-of-a-MAC-address-in-a-router) <br>Q 6 : [Do sites see and store MAC addresses? Either of your PC or the wifi device connecting to the 'net? : r/PrivacyGuides](https://www.reddit.com/r/PrivacyGuides/comments/w5m7yk/do_sites_see_and_store_mac_addresses_either_of/?rdt=57142) <br>Q 7 : is wifi router save the mac address of a connected device
- Q : related to wifi
	- Q 1 : How Hackers Spy on you from your own WiFi! : [How Hackers Spy on you from your own WiFi! - YouTube](https://www.youtube.com/watch?v=wf-b74ciHLc&ab_channel=TechRaj156)
- More about wifi-hacking via wifi-adapter + How to choose a wifi-adapter acc. to needs : <br>Timeline (16:57 - 21:20) [WI-FI Hacking Crash Course for Absolute Beginners [NEW] - YouTube](https://www.youtube.com/watch?v=rYA_BbgqbP4&ab_channel=whiteseccybersecurity)
- more about "`iwconfig`" command : [usage of iwconfig command](https://www.perplexity.ai/search/whats-the-use-PBuJlSaGQQ6R_2ul5wUnpw?s=u)

