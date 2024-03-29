#WAPT-notes  

---
### what we'll learn
> Lecture Name : Burp Suite #3 How Burp Suite Proxy Works? MITM Attack?
> 1) what's proxy
> 2) role/working of it
> 3) Practical Work : working of proxy in BurpSuite
> 4) task related to dark mode proxy (not important topic)

---
### what's Proxy
- Eg of Proxies : in classroom , u said proxy attendance to a friend <br>
	which mean that friend will do that work for u , if u're not going to college ✔️

### role/working of proxy
- `1st work of proxy` : To Filter websites
    - in college/office , some websites won't open like facebook , tiktok , etc.. so they blocked those websites , <br>
		so "how they block these websites" ✔️
    - Generally , internet allows every websites ✔️, so let's say u're in network team of an organization & u want to block   
        - Q : How u gonna block those websites which u don't want in ur organization ? ✔️
        	<br>Ans : 
			<br>1st) so whatever all the traffic/websites are coming , u need to check - means let's say a user writing "tryhackme.com"
        	<br>2nd) so first we'll check whether this website defined inside the allowed list or not
        	<br>3rd) but Q : how to check whether that website defined in the allowed list or not - Ans : so this done via proxy
	- this shows the first working of it i.e to filter websites means to allow some websites according to requirement <br>
		& don't allow some which are not needed
  	- Diagram explanation of how request/response done with proxy server : <br><img src="../../notes-pics/02-Module/08_lecture/08_lecture-0-M2.jpg" alt="" width="500"/>
		- in the middle aka proxy server
		- the request of client 1stly goes to - the Proxy server - then the main server (i.e web server of that website)<br>
			then the response of a web server goes to - to the proxy server - then to the client ✔️
		- Eg : if u're accessing "tryhackme.com" , so firstly , GET request of that website goes to the Proxy server <br>
			but the GET request don't go directly to the main web server (that's why the proxy server acting as MITM attack) ✔️
		- so the GET request will go - to the proxy server - now the proxy server will check that website exist or not ✔️
		- Now the proxy server will see whether that website is inside the allowed list or not , <br>
			so if that website in the allowed list then only the request will go to the web server of "tryhackme.com"  ✔️
		- then the web server will send the response - goes to the proxy server - then it goes to the client ✔️ 
		- but if that website is not allowed then the request goes from the client - <br>
			to the proxy server - & the proxy server will check & tell that this website is disallowed , <br>
			so the response (with a generic error shown to the client machine) will go back to the client directly <br>
			& the request will not go to the web server ✔️ <br>
	- so 1st work of proxy i.e to filter the websites : <br>
		means if there's a requirement then allow something & disallow something 
- `2nd work of proxy` : modify the request/response after intercepting
	- firstly , all the requests going via the proxy server & responses coming on the proxy server
	- if we want to test one or more websites then we can do changes on them (i.e requests & responses)
	- Eg : means whatever the GET request goes to the proxy server like u need "tryhackme.com" page , <br>
		so u can do changes on runtime cuz that request didn't send to the web server yet ✔️
	- Eg : let's say on a banking website , u're sending a GET request that bring my A/C number details & <br>
		that banking webapp is vulnerable
	- so generally , the GET request goes directly from client to the web server & <br>
		the server will bring ur A/C details - but in the middle , there is a proxy server , <br>
		so firstly the GET request go from client to the proxy server then we can change the A/C number <br>
		in the proxy server via BurpSuite. so we'll change the A/C number & that modified one will go to the web server ✔️
    - & the web server never able to know difference b/w both that <br>
		the actual A/C number send from the client & send by the proxy server - which one is original <br>
		cuz for the web server , the request came from the proxy server ✔️
	- Eg : there are 3 people , 1st friend said something to 2nd friend to tell the 3rd friend <br>
		but 2nd friend changed/modified that chat (of 1st friend) & told to 3rd friend 
		<br>- so 3rd friend never going to know that what 1st friend actually told me (i.e 3rd friend) ,
		<br>- u already know that sometimes friends exaggerate
		<br>- so middle friend is controlling all the things (like modifying , what to tell & what not to tell , forwarding & dropping) ✔️
    	<br>- let's say 1st friend was appreciating (about his 3rd friend) with 2nd friend but 2nd friend modified it & <br>
			said to 3rd friend that 1st friend was saying wrong things about u

### Practical Work : working of proxy in BurpSuite
- STEP 0 : setup VPN [Connect to TryHackMe labs using VPN ( OpenVPN client ) - Kali Linux](https://www.youtube.com/watch?v=IvUsXg8dKds&ab_channel=LearningWithTom)
- STEP 1 : Now let's ON the proxy - means in kali's terminal , run burpSuite as `burpsuite` command
- STEP 2 : go tryhackme.com/room/burpsuitebasics -> in "introduction" section, start the machine
- STEP 3 : copy the IP address which is given by tryhackme.com/room/burpsuitebasics
- STEP 4 : 
	- STEP 4.0 : go in BurpSuite -> proxy tab -> Options tab , output : u'll see default IP + port no. (i.e 127.0.0.1:8080)<br>
		Q : why we're defining BurpSuite's proxy default (IP + port no.) on the browser ✔️<br>
		Ans : cuz if we don't define on the browser - then BurpSuite won't be able to capture/intercept the requests & responses
	- to change the proxy (IP address & port no.)
		<br>either go in BurpSuite -> Proxy tab -> Options & add that IP address (which is given by tryhackme.com lab)
		<br>OR open firefox -> foxyProxy extension & click on "Burp" option (which has default (IP + port no.) configured)
	- STEP 4.1 : so we'll define the BurpSuite's default proxy (IP address & port) on the browser ,
		<br>go to firefox -> open foxyProxy extension -> select Burp
		<br>output : now firefox's IP address + portno. (i.e 127.0.0.1:8080)
	- STEP 4.2 : in firefox , write "10.10.33.100" & hit Enter
- STEP 5 : in burpSuite , on the intercept & in firefox , hit enter & u'll get the GET request of that IP address like this 
	<br><img src="../../notes-pics/02-Module/08_lecture/08_lecture-1-M2.jpg" alt="" width="500"/>
	- now u can either `forward`  or `Drop` this GET request just like 3 friend situation ✔️
	- or u can change/modify the GET request , so right click on empty area & <br>
		click on `Send to Repeater` option ✔️ but click on `forward` button
- STEP 6 : & turnoff the Intercept & all the things will save inside Proxy -> HTTP history ✔️
	- output : we'll get Juice shop <br><img src="../../notes-pics/02-Module/08_lecture/08_lecture-2-M2.jpg" alt="" width="500"/>
	- STEP 6.1 : click let's say on Apple Juice (1000ml) & we'll GET request in Burp Suite , <br>
		we can check all the request we made according to `time` like this <br><img src="../../notes-pics/02-Module/08_lecture/08_lecture-3-M2.jpg" alt="" width="500"/>
- STEP 7 : to change this GET request , then right click on left side bottom `Request` section & <br>
	click `Send to Repeater` (means modifying/changing the GET request & then sending to the server) ✔️
	- STEP 7.1  : in Repeater , change the product from `1` as `7` then we'll get 7 product as Response also <br>
		like this <br><img src="../../notes-pics/02-Module/08_lecture/08_lecture-4-M2.jpg" alt="" width="500"/>
	- Once u change from 1 to 7 inside the GET request then we'll get response for 7 reviews also 
		<br><img src="../../notes-pics/02-Module/08_lecture/08_lecture-5-M2.jpg" alt="" width="500"/>
	- so we changed the data & item goes to 7 i.e Green Smoothe
- STEP 8: we can run intruder  
	- STEP 8.1 : in Repeater -> right click on `Request` section & click `Send to Intruder`
	- STEP 8.2 : in burp Suite -> Intruder tab
		- we'll get updated `Target` 
		- in `Positions` tab (it's a main tab where we need to define where we want to do intruder) ✔️
	- STEP 8.3 : in `Positions` 
		- click on `clear` button
	- now we did from 1 to 7 but what if we want to run till 100 GET requests step by step automatically ✔️
	- STEP 8.4 : select that `7` & click on `Add %` button (which is aka marker) like this 
		<br><img src="../../notes-pics/02-Module/08_lecture/08_lecture-6-M2.jpg" alt="" width="500"/>
		- which means left & right numbers of 7 will change ✔️
	- STEP 8.5 : Intruder have 4 Attack modes/types : but select it as `Sniper`
	- STEP 8.6 : `Payloads` tab -> Payload type as `Numbers` 
		- in `Payload Options [numbers]` -> from as `1` , `To` as 10 & Step as `1` <br>
			(which means steps will increase by 1 like 1 , 2 , 3 , 4 etc...)
    - STEP 8.7 : click `Start Attack` button, now intruder will start & u'll get all those 10 items with 200 ok status code 
		<br><img src="../../notes-pics/02-Module/08_lecture/08_lecture-7-M2.jpg" alt="" width="500"/>
- if we do these 10 GET requests send via `repeater` then time taking increase , <br>
	even thou currently there are 10 GET requests only but what if we have 1000 requests , <br>
	so `intruder` will do automatically fast ✔️

### Ques

- Q 1) By default , the Burp Suite Proxy listens on only one interface. what is it ? use the format of IP:PORT <br>
	Ans : `127.0.0.1:8080`
- Q 2) Shortcut which allows to forward the request to Repeater ? <br>
	Ans : `Ctrl + R`
- Q 3) Shortcut to forward our request to intruder ? if we wanted <br>
	Ans : `Ctrl + I`
- Q 4) Burp Suite saves the history of requests sent through the proxy along with their varying details. <br>
	This can be especially useful when we need to have proof of our actions throughout a penetration test or <br>
	we want to modify and resend a request we sent a while back. What is the name of the first section <br>
	wherein general web requests (GET/POST) are saved? <br>
	Ans : `HTTP History` tab
- Q 5) Defined in RFC 6455 as a low-latency communication protocol that doesn't require HTTP encapsulation, <br>
	what is the name of the second section of our saved history in Burp Suite? These are commonly used in <br>
	collaborate application which require real-time updates (Google Docs is an excellent example here). <br>
	Ans : in `proxy` , one we have `HTTP History` but another we have WebSocket history
	- so server & client request & response shown/captured inside `webSocket History` tab, `Socket` -> used to make/build connection
- Q 6) Before we move onto exploring our target definition, let's take a took at some of the advanced customization <br>
	we can utilize in the Burp proxy. Move over to the options section of the Proxy tab and scroll down to Intercept Client Requests. <br>
	Here we an apply further fine-grained rules to define which requests we would like to intercept. <br>
	Perhaps the most useful out of the default rules is our only AND rule. What is it's match type? <br>
	Ans : URL
	- Proxy -> options -> in Intercept Client Requests , in `And` , what's the `Match Type` i.e URL
- Q 7) How about it's 'Re la tionship'? In this situation, enabling this match rule can be incredibly useful <br>
	following target definition as we can effectively leave intercept on permanently (unless we need to navigate without intercept) <br>
	as it won't disturb sites which are outside of our scope - something which is particularly nice <br>
	if we need to Google something in the same browser. <br>
	Ans : is in `target scope` 
	<br>- in `Target` tab -> `site map` -> u see that services , etc stuff are running of firefox which are intercept by BurpSuite
	<br>- but if i want to look at this only for testing i.e <br><img src="../../notes-pics/02-Module/08_lecture/08_lecture-8-M2.jpg" alt="" width="500"/>
	<br>- cuz let's say u're typing something on google research work then all the stuff , whatsapp running & <br>
		messages are coming frequently will be intercept by Burp Suite 
	<br>- so this section gets long , right click on that localhost -> Add to Scope -> click No , <br>
		click on that filter tab -> check `Show only in-scope items` like this <br><img src="../../notes-pics/02-Module/08_lecture/08_lecture-9-M2.jpg" alt="" width="500"/>
	<br>- so all those unnecessary things go away & only targeted thing will get visible for testing

---
### End of the lecture (Doubts)
- Turn On the Dark Mode in Burp Suite : user options -> Display -> there u go
