#WsCubeTech-CEH-notes

---
### What we'll learn 
> Lecture Name : Layers Of Internet & UA & MAC Address Change
> 1) intro - Layers of internet
> 2) what is HTTP
> 3) What is URLs
> 4) Types of Webs on Internet : Surface Web , Deep Web , Dark Web
> 5) Tor Browser : accessing Deep Web & Dark Web
> 6) Ways to be anonymous

---
### intro - Layers of internet
- its a part of how to be anonymous on the internet - which is based on the address/URL
- Q : what's the internet Rule ? 
	- Q : what do we need to access anything OR a file on the internet ✔
	- Ans : only a IP address (of a website) - can't be , cuz if u just write the IP address or domain name <br>of Facebook then can u reach at ur FB Profile directly 
	- IP address will be used on internet <br>Q :  means u search the IP address of FB - then FB show the login page - & u login inside FB - then can u access ur FB account <br>Ans : No
	- cuz it's a Internet Rule i.e to access anything on the internet - we need a URL <br>- URL : is a address & it's a only way to access any file/thing/etc ✔
	- Q : if u search directly i.e Kapil's FB profile on FB website - then can u get directly the Kapil's profile <br>Q : u need a hacking page of wscubetech , so if u search wscubetech & can the search will show hacking page of wscubetech ✔ <br>Ans : either <br>1) u have to go inside wscubetech & visit on hacking page manually <br>2) OR search on google <br>3) OR URL
	- URL : Uniform Resource Locator
- Q : from where do we get the URL of anything - means who provide URL ✔
	- so URL address brings/given by search engines
	- Q : what is search engines<br>Ans : Eg : google , yahoo , duckduckgo , etc<br>- these search engines have a responsibility i.e keeping URL (means address) of each thing ✔
	- Eg of URL :<br>> STEP 1 : search "wscubetech hacking" , output : u'll get ethical hacking page directly - on search list <br> Q : why + How we got the ethical hacking page directly ✔<br>Ans : Cuz - google search engine has a direct address i.e "`wscubetech.com/online-ethical-hacking-course.html`" <br>- without a complete address/URL , we can't reach there - where we want to go ✔ <br>- means we don't have that ethical hacking URL or if we don't search "hacking" <br>then we'll directly come to this site "wscubetech.com" page ✔
	- without search engines , we can't access any address on internet ✔
- Q : why we can't access anything without search engines + importance of search engines✔
	- let's say u know ur FB profile , u also know the IP address of FB 
	- Q : can u tell me - do u know complete address/URL of ur FB profile account <br>Q : Eg : can u remember always that complete URL/address of hacking page of wscubetech <br>OR can u type that complete address by urself manually
	- Ans : No , cuz as a human - we can't remember that long URL/address - even we can't remember IP address of anything <br>- so direct address of something will be provided by search engines ✔

### what is HTTP
- used for Core Communications 
- it uses TCP - to send & receive packets/data ✔
- it send & receive packets/data - of requests & Responses by using TCP protocol ✔

### What is URLs
- URL : Uniform Resource Locator <br>URI : Uniform Resource Identifier
	- URL vs URI : both means same almost
	- for more b/w URI vs URL <br>> [URI vs URL: Definition, Key Differences, and More](https://www.hostinger.com/tutorials/uri-vs-url) <br>> [Difference between URL and URI - GeeksforGeeks](https://www.geeksforgeeks.org/difference-between-url-and-uri/) <br>> answer from AI : [URI vs URL](https://www.perplexity.ai/search/URI-vs-URL-daCSNsl9Qb.XGP3Vn0JenA?s=u)
- it's a web Resource Unique identifier : means it uniquely identifies each resource 
- Eg of URL Structure : `protocol://hostname[:port]/[path/]file[?param=value]`
	- 1st : protocol will come
	- 2nd : hostname - means domain name like "wscubetech.com"
	- 3rd : `[:port]` - will be not visible to u , but behind the scene it's there
	- 4th : `[path/]file` - means which file u want to access
	- 5th : `[?param=value]` (it's also a part of Penetration testing)
		- Real Life Examples <br>> Eg 1 : `a=15` - means "a" is parameter & "15" is a value of "a" parameter <br>> Eg 2 : `a+b=15` - means "a+b" is a parameter & "15" is a value of "a+b" parameter
		- Actual Examples <br>> Eg 1 : in website , there are pages - like u want to access a page `page=1` <br>- "page" is a parameter & "1" means we're on a page no. 1
- Eg : `http://ws.com:80/auth/login.ashx?uid=129`

### types of Webs on internet : Surface Web , Deep Web , Dark Web
- whatever we're doing like surfing on the internet , etc - Everything done inside the browser
- we'll see more about different Webs on internet <br>- Pic of different Webs : <br>![[23_lecture-0-M3.jpg | 500]]
- normal humans accessing + using + viewing only 5% of internet & <br>95% internet is hidden from normal users 
- Surface Web : 
	- eg : FB , yt , google , etc
	- means whatever things u're getting (after searching in ur browser) from internet - all these comes in Surface web ✔
	- for Surface web , ✔<br>- google , etc search engines are made <br>- & browsers - chrome , etc
- Deep Web : 
	- contains those things (which comes under the "Surface web") - means u can't bring those details via searching ✔
	- Eg : bank Entries , hospital medical records of a person , etc - which can't get details via searching ✔
	- So Those sort of things are kept inside Deep Web - which can't be accessed easily & can't get via searching ✔
	- so those 95% stuff comes inside Deep Web 
- Dark Web : 
	- it's a part comes inside Deep Web 
	- Deep Web vs Dark Web : ✔ <br>- in Deep Web , only important + useful information kept due to security purpose - in order not to show on search results <br>- in Dark Web , all the illegal (information + activities) done
	- Eg of Dark Web : child trafficking , selling body parts , red room , etc
	- ⚠️ Danger : not allowed to go in Dark Web , if cyber Police find u in Dark web for illegal activities <br>then it's becomes difficult for u
- Hidden Web
	- after these 3 Webs , there is a another one i.e Hidden Web 
	- it's a part/world of Internet - which is not (accessed + discovered) yet & unknown from normal users ✔
	- Eg 1 : let's say - u made a website & u shared the website with Kishan , only u & kishan knows about that website <br>& no one knows about it , so this information comes inside Hidden Web ✔
- Examples : 
	- Eg 2 : Q : Now Kishan shared that website link with somewhere & now 100-500 people knows about it , <br>So which category of Web - this information or the website comes ✔<br>Ans : Deep Web , cuz only few people knows about it - but those people can't access the website
	- Eg 3 : Q : Now those 100-500 people shared that website with others - now people coming 1-2 Lakh on it <br>- due to this , by searching that website is coming on search results - which Category of web <br>Ans : Surface Web - cuz it's coming on search results by search engines
	- Eg 4 : Q : Now many people knows about that website & <br>let's say u started illegal activities with kishan - to get the profit , which category of web <br>Ans : Dark Web

### Tor Browser : accessing Deep Web & Dark Web
- why we need Tor Browser
	- Q : did u try to access Deep Web , Dark Web via ur Chrome Browser or any brower <br>Ans : Not Possible , cuz need a special Search Engine i.e Onion - is a search engine of Tor Browser ✔
	- Tor Browser used to access Deep Web , Dark Web - mostly it used for accessing Dark Web 
- in terms Security : is Tor Browser secure 
	- Yes , cuz its consider most secured Browser
	- Securities + Reasons : How Tor Browser is Secure ✔
		- 1st : this browser is not used for normal surfing on the internet , <br>in order to access those stuff - we can't use normal browsers
		- 2nd : u can remember normal links like "google.com" , etc <br>but u can't  remember links which are search in Tor Browser
			- Eg : 12102BA62A3062090.onion - somewhat a link/URL will looks like in TOR browser <br>- in Tor Browser , each link/URL ends with ".onion" extension 
			- even if remember a link/URL in TOR browser , then after sometime time - that link will be changed <br>- let's say someone shared that updated onion link on telegram - so due to this , even that link <br>changed again & again - then that person will share again & again - then every one access that link <br>- so that's why 3rd Reason comes
		- 3rd : due to issue of 2nd reason , in Tor browser - three-layers of IP security is implemented
			- means when u access TOR browser - then by-default Tor Browser - implement 3-layers of IPs
			- 1st IP : will show in US <br>2nd IP : will show in china <br>3rd IP : will show in canada <br>- & somewhere ur system will be behind mostly these 3 different IPs - in order to hide ur actual IP-address ✔
			- 1st IP : is very much secure with too much configurations - means u can't hack it very easily <br>& other 2nd & 3rd IPs - are also much secure <br>- but 1st IP is more secure than both 
			- so when a victim's system sitting behind those 3 different changing IPs
				- let's say u trace all 3-layers of IPs - in order to trace/hack the Victim's system
				- Eg : Q : let's say that Victim do illegal activities & u want to hack his/her system/server <br>that victim uses TOR browser & the Victim selling guns & u as a fake person - u want to buy <br>so what will u do to access/hack the Victim's system/server
				- Ans : in TOR browser , that "3-layers of IPs security" - will change current the IP address of Victim's system
					- means the more u connect & disconnect - continuously the IP address will change
					- when u order then the Victim will might give a form to fill <br>so u can attach virus file or link in that form/server (where that form hosted) & send on the Victim's system <br>- so doesn't matter how much IPs are changed - at the end , the file/link will goes to the Victim's system/server <br>- & once the Victim will open - then the Virus will get execute <br>then we'll get the info about the Victim's system/server ✔
				- but this method also tried by many hackers earlier
			- But TOR browser people are v. smart - they also implemented the security for this issue 
		- 4th : IP validator
			- Tor Browser people implemented the IP Validator security - due to issue in 3rd security
			- in IP validator , TOR browser's team made a list which contain many IP addresses <br>& TOR browser's team said - if a person have a IP address (out of those IP addresses inside the list , <br>not from out the list) - then only that person can reach to this IP-address/link/URL "12102BA62A3062090.onion"
			- But attacker change many IP-addresses again & again <br>- then one IP address (out of those IP addresses inside the list) got matched with the attacker's IP address <br>- due to this , attacker reached & "IP validator" security got broke
			- that's why 5th security implementation comes
		- 5th : Mac validator
			- MAC : means physical address of a device
			- now TOR Browser's team made a list of MAC addresses <br>& they said - if a person have a MAC address (out of MAC addresses inside the list) <br>- then only that person can reach to the URL/IP-address/link "12102BA62A3062090.onion"
			- but again - attacker again & again continuously changed the MAC address <br>then a MAC addresses got matched with a MAC address (which is inside the list)
			- again they implemented a 6th security
		- 6th : user-agent validator
			- Q : what kind of details carried by user-agent to send to the server <br>Ans : Browser & OS details
			- TOR Brower's Team made a list of user-agents <br> if a person's user-agent got matched with the user-agents list - only then that person can access the URL
			- but attacker also break the user-agent validator security
		- due to this , one by one security broke , however - if once 2 securities combine together <br>like IP validator + MAC validator = not possible to break this security - cuz it'll more than 1year to crack the security
		- so attackers started to break each securities by changing one by one <br>like changing user-agent -> then MAC address -> then IP address ✔
		- so why not if these securities are used by TOR browser - then we can also implement in our system <br>- so all the Hackers started combining (user-agent + IP-address + MAC address) to be anonymous on internet ✔
		- Pic - TOR browser securities <br>![[23_lecture-1-M3.jpg | 500]]

### Ways to be anonymous
> 1. Changing User-agent details
> 2. Changing MAC address 
> 3. Changing IP address (in 24th lecture)
1. STEPS : changing the user-agent details
	- STEP 1 : install a Chrome extension - Random User-Agent (Switcher) : [Reviews: Random User-Agent (Switcher)](https://chromewebstore.google.com/detail/random-user-agent-switche/einpaelgookohagofgnnkcfjbkkgepnp/reviews)
	- STEP 2 : turn off the "Random user-agent" extension & open [whatsmybrowser](https://www.whatsmybrowser.org/) <br>- output : this website will show ur Public Static IP address , browser + OS details taken by user-agent <br>> STEP 2.1 : to change the user-agent details , turn ON that chrome extension
	- Note : keep that Chrome extension OFF - cuz it'll create issue during accessing a website 
2. STEPS : Changing MAC address
	-  STEP 1 : open kali terminal , run `ifconfig` - to check the MAC address
		- output : <br>![[23_lecture-2-M3.jpg | 500]]
		- in kali OS , "eth0" : means internet & "ether" : means MAC address
		- `imp Note ⭐` :  in order to change/fake the MAC address of a device (instead of showing actual MAC address) ,
			- firstly , we need to close that thing - then only we can change/fake that thing <br>- means in kali OS , MAC address is inside "eth0" - so firstly , close the "eth0"
			- changing MAC address before closing the "eth0" - then issues will come
			- Eg : we can't repair engine of a car when a person driving a car
	- STEP 2 : closing "eth0" , run `ifconfig eth0 down`
		- "eth0" is a software device , <br>so u can put an device name which u want to close on the place of "eth0" in this command ✔
		- output : in kali , network will disconnected <br>![[23_lecture-3-M3.jpg | 500]]
	- STEP 3 : in kali , copy the actual MAC address
		- STEP 3.1 :  changing actual MAC address , run `ifconfig eth0 hw ether 00:0c:29:55:11:4c `
			- in this command , ✔<br>> "hw" : means hardware - cuz MAC address is a hardware address <br>> "ether" : means MAC address was inside "ether" - that's why "ether" came <br>> then copy the actual MAC address
			- Q : what details have in a MAC address ✔<br>Ans : first 3-pairs - contains vendor/company details (who made the device) & last 3-pairs - contains device ID
			- so we need to hide the details of our device ID , not the Vendor/company details <br>- means we'll only change the last 3-pairs in a MAC address ✔
			- Q : what's the range of MAC address OR how many combinations are used to make a MAC address ✔<br>Ans : a-f & 0-9
		- STEP 3.2 : changing only last 3-pairs (i.e device ID) of MAC address , run `ifconfig eth0 hw ether 00:0c:29:a3:99:53`
		- STEP 3.3 : turn ON the "eth0" , run `ifconfig eth0 up`, output : kali's network is connected
		- STEP 3.4 : run `ifconfig` , output : now MAC address has been changed <br>![[23_lecture-4-M3.jpg | 500]]
		- now instead of doing all of these manually by commands , use a tool → "macchanger"
		- STEP 3.5 : run `macchanger` , output : it's syntax "`macchanger [options] device-name`"
			- STEP 3.5.1 : run `macchanger --help` , output : options of "macchanger" tool
			- `-s OR --show` option of "macchanger" tool : means show the current & permanent MAC address of a system ✔
			- STEP 3.5.2 : run `macchanger -s eth0` , output : <br>![[23_lecture-5-M3.jpg | 500]]
			- Note : u can't change the permanent MAC address , but u can change the Current MAC address ✔
			- 3 layers in each MAC address ✔
				- 1st layer : current MAC address <br>2nd layer : Permanent MAC address <br>3rd layer : New MAC address
				- New layer of MAC address  : means that MAC address will come (in New Layer) which is just changed <br>Current layer of MAC address : contain previous MAC address <br>Permanent Layer of MAC address : contain actual MAC address of a device - which will never change
				- Eg : by-default Current layer - contain the Permanent MAC address <br>- 1st time , if u change the MAC address : then that MAC address comes in New layer <br>- 2nd time , if changing MAC address : then that MAC address (of New layer) comes in Current Layer <br>& a MAC address in New layer vanished <br>- 3rd time , if changing MAC address : then that new MAC address again comes in New layer <br>- Permanent MAC address will not change , but MAC address of (Current Layer + New Layer) will change ✔
				- so both Current Layer & New Layer of MAC address = keep "Permanent MAC address" secure ✔ <br>- due to this , no one can easily get the MAC address of a device - until that person hack the device ✔ <br>- means if someone hacked ur system , then no point of hiding the Permanent MAC address ✔
			- other options of "macchanger" tool <br>> `-e OR --ending` : means this option will change only the last 3-pairs of MAC address <br>> `-a OR --another` : means it'll set random Vendor MAC i.e first 3-pairs <br>> `-p OR --permanent` : means reset the MAC address into permanent address <br>> `-r OR --random` : means set fully random MAC <br>> `-l OR --list` : means it'll show only the first 3-pairs (i.e vendor MAC) of all the companies around the world ✔
			- useful option is "-e OR --ending"
			- STEP 3.5.2 : run `macchanger -l` , output : only first 3-pairs of MAC address will be shown of each companies<br>![[23_lecture-6-M3.jpg | 400]]
			- STEP 3.5.3 : run `macchanger -s eth0` , output : just to check <br>> then run `macchanger -e eth0` , output : a new mac address added in "New layer of MAC address" <br>> then run `macchanger -e eth0` , output : MAC address (which is inside New Layer MAC) will go inside Current MAC <br>& in New Layer Mac - will get a new MAC address <br>- overall output : <br>![[23_lecture-7-M3.jpg | 500]]
		- Cons of "macchanger" tool : ✔<br>when a Kali system gets restarted/rebooted - then by-default Permanent MAC address will be set - inside "eth0"
		- so to void this cons of "macchanger" tool : when u're hacking/attacking to the Victim's system <br>- then u can perform these "macchanger" commands <br>- but if u forgot then issue will come ✔
		- solution : make a program - due to which , MAC address gets changed automatically ✔
		- STEP 3.6 : making a program - in order to change MAC address automatically - when system gets rebooted
			- STEP 3.6.1 : run `gedit mac.sh` - then inside the file , write these commands <br>> 1st line : `macchanger -e eth0` <br>> 2nd line : `macchanger -e eth0` <br>> 3rd line : `macchanger -e eth0`
			- `imp note ✅` : we wrote "-e" : cuz we want to change the last 3-pairs of MAC address & "eth0" : is a device name<br>Q : why we wrote the same command 3 times ✔<br>Ans : cuz permanent MAC address will be hidden from both (Current + New layers MAC address) <br>- by-default , "Current MAC address" contain permanent MAC address <br>- 1st time , running the command : then the MAC address will go inside New layer MAC address <br>- 2nd time , running the command : then the MAC address (of New Layer) will go inside "Current Layer MAC" <br>- 3rd time , running the command : then the MAC address will come inside "New layer MAC"
			- STEP 3.6.2 : save the file
			- STEP 3.6.3 : giving executable permission , run `chmod +x mac.sh`
			- to reboot a kali system , there's a service i.e "crontab" ✔ <br>- "crontab" service : means during rebooting process , it runs those programs which are required ✔
			- STEP 3.6.4 : editing "crontab" service , run `crontab -e`
				- `-e` : means editing mode
				- after "GNU nano 7.2" text , write in a new line i.e `@reboot /home/kali/mac.sh` - then "Ctrl + S" - then "CTRL + X"
				- output : <br>![[23_lecture-8-M3.jpg | 500]] <br>![[23_lecture-9-M3.jpg | 500]]
				- now a new crontab installing
				- currently service of "crontab" is not started yet - cuz we just edited it
			- STEP 3.6.5 : start service of "crontab" , run `service cron start`
			- STEP 3.6.6 : run `systemctl start cron` -> this command will start the crontab service in background
			- STEP 3.6.7 : run `update-rc.d cron defaults` -> this command will run crontab service by-default automatically
			- now whenever we restart the Kali system , then automatically - MAC address will get changed
			- STEP 3.6.8 : run `ifconfig` - then copy this MAC address - & paste in a file to remember
			- STEP 3.6.9 : run `reboot` , output : in kali terminal , MAC address has been changed

---
### Homework
1. 

---
### End of the lecture (Doubts) :
1. 


