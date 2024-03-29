#WAPT-notes  

---

### what we'll learn
> Lecture Name : Burp Suite #1 Introduction | Installation | Configuration | Proxy
> 1) Burp Suite intro
> 2) it's installation
> 3) it's configuration
> 4) how to use it & it's different major components
> 5) it's proxy component intro

### Aim of the lecture
- after watching complete lectures of BurpSuite , u don't need to watch anything else for it
- Burp Suite - most imp tool ✔️️

### Prerequisite
- must know prev. 5 lectures of Basics of Web Fundamentals 

### References
- [TryHackMe: Burp Suite: Basics— Walkthrough | by Jasper Alblas | Medium](https://medium.com/@JAlblas/tryhackme-burp-suite-basics-walkthrough-209ab703d6a1)
- [TryHackMe- Burp Suite Walkthrough | by Katjah Smith👩🏽‍💻 | System Weakness](https://systemweakness.com/tryhackme-burp-suite-walkthrough-c71e10b1112)

---

### 1. BurpSuite intro
- reference : [TryHackMe | Burp Suite: The Basics](https://tryhackme.com/room/burpsuitebasics)
- it's a framework for WAPT cuz it's a collection of different tools like decoder , etc
- pentesting/penetration testing both means same
- Q : why Burp Suite called as defacto tool <br>
	Ans : it's a defacto tool means standard tool - means if someone knows WAPT or he/she do bug bounty , <br>
	webapp sec/security , etc - those people know already burp suite
	- without burpSuite it's not possible unless a person using scanner 
- it's major components are : Proxy , intruder , decoder , Sequencer, Extender , Repeater , etc

### 2. Installation
- diff. b/w Community Edition vs Pro version of BurpSuite
	<br>- in Community version : not get webapp scanner (which used to find vulnerabilities automatically)
	<br>- but community version is fine to do major work
- in kali Linux OS
    - BurpSuite Community Version + Java JRE already installed
	- & command to run BurpSuite on Kali terminal i.e `burpsuite`
- in winOS 
	- portswigger - is a company who made the BurpSuite software/product
	- STEPS to download : 
		- STEP 1 : go to website [Burp Suite](https://portswigger.net/burp)
		- STEP 2 : Products tab -> Burp Suite Community Edition -> choose OS & download it
		- STEP 3 : download java JRE cuz burp Suite requires [Java JRE](https://www.java.com/en/download/)

### 3. Gettin' CA Certified
- BurpSuite has a SSL Certificate 
    - STEP 1 : like open it -> go to it's `proxy` tab -> in `intercept` tab , output : u'll see `Open Browser` btn
    - in BurpSuite , if u get this popup error <br><img src="../../notes-pics/02-Module/06_lecture/06_lecture-0-M2.jpg" alt="" width="500"/> <br>
		to fix it , go to `Project Options` tab -> `Misc` tab -> Embedded Browser -> <br>
		check the checkbox i.e Allow the embedded browser to run without a sandbox
- intercepting requests via BurpSuite with "Open Browser" burp suite feature
	- STEP 1 : go `Proxy` tab -> intercept tab -> click on `Open Browser` btn ✔️
	- STEP 2 : now when u type like `demo.testfire.net` website , then inside BurpSuite <br>
		output : that website gets intercept , we got the GET request ✔️ 
		<br><img src="../../notes-pics/02-Module/06_lecture/06_lecture-1-M2.jpg" alt="" width="500"/> <br>
		which u already seen in web fundamentals
	- Q : how GET request comes inside the client machine (browser) ✔️<br>
		Ans : cuz here we didn't setup the proxy stuff cuz we're using embedded browser of BurpSuite <br>
		& which website is captured/intercept will be shown in `HTTP history` tab 
        <br>- the browser (on which proxy is not configured) - then if u do any searches on that browser <br>
			then those searches's requests can't be intercepted via burpsuite
- intercepting requests via BurpSuite without using "Open Browser" BurpSuite feature
	- so we can't intercept requests on which we're running browser manually (like firefox , chrome) <br>
		cuz we didn't step the BurpSuite's proxy default (IP + port no.) in these browsers (which are not embedded browser of BurpSuite)<br>
		& in old version of burp Suite , `open browser` btn feature are not there
	- STEP 1 : open firefox -> settings -> preferences , search `xy` -> network settings
	- STEP 2 : click on `settings` btn -> select only `manual proxy config` & others should be unchecked <br>
		& tick the `Also use this proxy for FTP & HTTPS` if u want & keep the "HTTP proxy" as `127.0.0.1` (which is a localhost) <br>
		& port as `8080` (means both default localhost IP + port no. are of BurpSuite app) like this 
		<br><img src="../../notes-pics/02-Module/06_lecture/06_lecture-2-M2.jpg" alt="" width="500"/>
	- STEP 3 : click ok
	- STEP 4 : in BurpSuite -> Proxy tab -> options tab -> localHost must be same as we set/define inside the browser <br>
		<img src="../../notes-pics/02-Module/06_lecture/06_lecture-3-M2.jpg" alt="" width="500"/>
	- Q : why now BurpSuite act as a MITM (man in the middle attack) OR using it for MITM ✔️
		- Ans : on the browser , now whatever GET request we type like `test.php.vulnweb.com` <br>
			& once u hit enter - then GET request will go/hit on the server (as earlier we learned in web-fundamentals) <br>
			& if the server have that request or IP address of domain name <br>
			then the response will be send (in the form of data/page) to the client - generally this happens
		- but now , the request directly goes to burpSuite (instead to the server) cuz Burp is a `proxy server` ✔️
		- Diagram : <br>
			<img src="../../notes-pics/02-Module/06_lecture/06_lecture-4-M2.jpg" alt="" width="500"/>
    	- when we hit the request for the website (like "test.php.vulnweb.com") <br>
			then the request will not go directly to the web server , the request will go to the middle i.e the BurpSuite <br>
			cuz `Burp Suite` is a `proxy server` ✔️
			Q : Why this will happen ✔️<br>
    		Ans : cuz we gave a port of that localhost 
    	- `imp Note ✅` : so firstly request will go from Client - to the Burp Suite proxy server - then we'll intercept the request <br>
    		& after intercepting the request , if u (as a hacker) want to forward the request to the server <br>
    		then only request will go the server
    		- then the server's response came - to the burpSuite Proxy server - then client <br>
    			so this is MITM attack , Role of the proxy server is to intercept each request & responses also ✔️
    - STEP 5 : in BurpSuite -> Proxy tab -> Intercept tab , keep the "Intercept is OFF"
        - STEP 5.0 : on firefox -> write `testphp.vulnweb.com` & hit enter
		- STEP 5.1 : right now , in Proxy tab -> Intercept -> intercept is off , but if u keep it off then still we'll get <br>
    		that website's requests in "HTTP history" tab of BurpSuite - but to ON the intercept - then click on `Intercept is on` btn
    - STEP 6 : Now in BurpSuite -> Proxy tab -> Intercept tab , keep the "Intercept is ON" 
		- STEP 6.1 : on firefox -> write `testphp.vulnweb.com` & hit enter
    	- output : once u hit the request then a GET request intercept by burpsuite
        - STEP 6.2 : in burp Suite -> Proxy tab -> Intercept tab , <br>
			if we click on "forward" btn - only then a GET request goes to the server
      	- STEP 6.3 : click on "forward" btn , output : a Get request goes to the server
    - STEP 7 : now we'll get a response from the server , so to check the response 
    	- STEP 7.1 : go Proxy tab -> HTTP history
    	- STEP 7.2 : & then double click on that URL , u'll get the response like this <br>
			<img src="../../notes-pics/02-Module/06_lecture/06_lecture-5-M2.jpg" alt="" width="500"/>
		- in pic , left side panel = a GET request & right side panel = a GET response
    	- output : so we got a response as `200 OK` , 
			<br>- we got a HTML code (which u can render the page there only - click on `render` btn)
			<br>- & in Response panel , server's (type + version) showing - cuz the website is vulnerable
	- intercepting via BurpSuite (issue with https that's why setting up SSL Certificate )
		- `testphp.vulnweb.com` - is a http website 
		- `imp note ✅` : we'll get issues with HTTPS when we intercept <br>
			cuz each `HTTPS` website need a SSL certificate (like https://www.google.com) <br>
			but HTTP websites doesn't need SSL certificate ✔️
		- Eg : in firefox -> write https://demo.testfire.net then we'll get error <br>
			<img src="../../notes-pics/02-Module/06_lecture/06_lecture-6-M2.jpg" alt="" width="500"/>
		- to avoid/skip this warning , installing SSL certificate
			- we're running a proxy server on `127.0.0.1:8080`
			- STEP 1 : so go that browser (only on which u have done the configuration BurpSuite Proxy server) <br>
				& then write http://burp & hit enter
    			- output : now u'll get the page of burp suite <br>
					<img src="../../notes-pics/02-Module/06_lecture/06_lecture-7-M2.jpg" alt="" width="500"/>
				- this page gives CA (certification authority) , it gives the certificate
			- STEP 2 : click `CA Certificate` btn & download it
			- STEP 3 : in firefox -> settings -> preferences -> search - certificate
			- STEP 4 : click `view certificate` btn -> import -> open it
			- STEP 5 : check both the checkboxes -> click ok -> then ok , output : now CA certificate is configured in that browser
			- STEP 6 : in burp Suite -> Proxy tab -> Intercept tab -> turn off the `intercept` btn
			- STEP 7 : go to the browser & reload that website page again , <br>
				output : so u'll not get that same error again & now that website is now HTTPS website
		- `imp note ✅` : role/purpose of SSL certificate in HTTPS
			- each HTTPs website needs a SSL certificate , so that website/webapp send the request/data to the web server <br>
				that data/request will be in encrypted ✔️
			- Eg : <img src="../../notes-pics/02-Module/06_lecture/06_lecture-8-M2.jpg" alt="" width="500"/>
				- u'll get verified by : PortSwigger cuz on firefox , we installed the SSL certificate of PortSwigger ✔️ <br>
					due to this , now all the requests goes encrypted
				- means each HTTPS website will get intercept by BurpSuite & no error will come <br>
					cuz SSL certificate installed on this browser ✔️
    	- u can skip all these of "to avoid/skip this warning , installing SSL certificate" , <br>
			if u use `Open Browser` feature (which is embedded browser) of burp Suite <br>
			so last 2 steps done if u're using old version of burp suite which hasn't have `Open browser` btn burp Suite feature
    	- we have `foxyProxy` firefox extension - which u can use <br>
			if u don't wanna follow steps of "to avoid/skip this warning , installing SSL certificate" <br>
    		<img src="../../notes-pics/02-Module/06_lecture/06_lecture-9-M2.jpg" alt="" width="500"/>
    		- click on Option , u can add Proxy server & see Anuj Sir already setup a Burp Proxy server as `127.0.0.1` like this <br>
    			<img src="../../notes-pics/02-Module/06_lecture/06_lecture-10-M2.jpg" alt="" width="500"/>
    		- the movement he want to use Burp proxy , he'll click on that Burp & if he wants to off the proxy , <br>
    			then he'll click on `Turn Off (user firefox settings)`

---
### End of the lecture (Doubts)

