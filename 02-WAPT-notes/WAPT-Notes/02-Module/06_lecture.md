#WAPT-notes  

---
### Overview
- BurpSuite intro , installation , configuration
- Burp Suite - most imp tool ✔

### Aim of the lecture
- after watching complete lectures of BurpSuite , u don't need to watch anything else for it

### what we'll learn
- Burp Suite intro
- it's configuration
- how to use it & how to use it's different major components

### what we'll learn in this lecture
- Burp Suite intro
- it's installation
- it's configuration
- how to use it
- it's proxy component introduction

### Prerequisite
- must know prev. 5 lectures of Basics of Web Fundamentals 

### References
- [TryHackMe: Burp Suite: Basics— Walkthrough | by Jasper Alblas | Medium](https://medium.com/@JAlblas/tryhackme-burp-suite-basics-walkthrough-209ab703d6a1)
- [TryHackMe- Burp Suite Walkthrough | by Katjah Smith👩🏽‍💻 | System Weakness](https://systemweakness.com/tryhackme-burp-suite-walkthrough-c71e10b1112)

---

### Topics - Explanation

Reference : [TryHackMe | Burp Suite: The Basics](https://tryhackme.com/room/burpsuitebasics)

1) <u>BurpSuite intro </u>
	- reference : [TryHackMe | Burp Suite: The Basics](https://tryhackme.com/room/burpsuitebasics)
	- it's a framework of WAPT cuz it's a collection of different tools like decoder , etc
	- pentesting/penetration testing both are called same
	- *why it's called defacto tool* 
		- it's a defacto tool means standard tool - means if someone knows WAPT or he/she do bug bounty , webapp sec/security , etc.. those people know already burp suite 
		- without burpSuite it's not possible unless a person using scanner 
	- it's major components are : `Proxy` , `intruder` , `decoder` , `Sequencer`, `Extender` , `Repeater` , etc
2) <u>Installation</u>
	- *diff. b/w Community Edition vs Pro version of BurpSuite* 
		- in Community version : not get webapp scanner (which used to find vulnerabilities automatically)
		- so community version is fine to do major work
	 - *in kali Linux OS*
		- u'll get BurpSuite Community Version & Java JRE already installed 
		- command to run burpsuite on Kali Linux terminal : `burpsuite`
	- *in win. OS ,* 
		- download : [Burp Suite - Application Security Testing Software - PortSwigger](https://portswigger.net/burp)
		- portswigger - is a company who made the BurpSuite software/product
		- STEPS to download : 
			- STEP 1 : go to website [Burp Suite](https://portswigger.net/burp)
			- STEP 2 : Products tab > Burp Suite Community Edition > choose OS & download it
			- STEP 3 : download java JRE cuz burp Suite requires [Java JRE](https://www.java.com/en/download/)
3) <u>Gettin' `CA` Certified</u>
	- BurpSuite has a SSL Certificate like when u open it , go to it's `proxy` tab , in `intercept` tab , u'll see `Open Browser` button
	- in BurpSuite , if u get this popup error ![[WAPT-lecture-6-0.jpg]]
		- to fix it , go to `Project Options` tab > `Misc` tab > Embedded Browser > check the checkbox i.e Allow the embedded browser to run without a sandbox
	- *intercepting via BurpSuite with `Open Browser` burp suite feature*
		- now go `Proxy` tab > intercept tab > click on `Open Browser` button ✔
		- now when u type like `demo.testfire.net` webite , then inside BurpSuite that website gets intercept like this ✔ ![[WAPT-lecture-6-1.jpg]]
		- which u already seen in web fundamentals , how GET request comes inside the client machine (browser)
		- here we didn't setup the proxy stuff cuz we're using embedded browser
		- & which website is captured/intercept will be shown in `HTTP history` tab ✔
		- the browser on which proxy is not configured then if searching stuff happen on that then we can't intercept the via burpsuite
	- *intercepting via BurpSuite without using `Open Browser` burp suite feature*
		- so we can't to intercept what we're running browser manually cuz in old version of burp Suite , `open browser` button feature are not there
		- STEP 1 : open firefox > settings > preferences , search `xy` > network settings
		- STEP 2 : click on `settings` button > select only `manual proxy config` & others should be unchecked & tick the `Also use this proxy for FTP & HTTPS` if u want & keep the HTTP proxy as `127.0.0.1` (which is a localhost) & port as `8080` like this ![[WAPT-lecture-6-2.jpg]]
		  - STEP 3 : click ok
		  - STEP 4 : in BurpSuite > Proxy tab > options tab > localHost must be same as we set/define inside the browser ![[WAPT-lecture-6-3.jpg]]
		  - STEP 5 : using burpSuite for MITM (man in the middle attack)
			  - STEP 5.1 : on the browser , now whatever GET request we type like `test.php.vulnweb.com` & once u enter then GET request will hit on the server
			  - & if the server have that request or IP address of it then the response will be send data/page to the client - generally this happens
			  - but right now , the request directly goes to burp Suite instead to the server cuz Burp is a `proxy server`  ✔
			  - Diagram : ![[WAPT-lecture-6-4.jpg]]
			- when we hit the request for that website then the request will not go directly to the server , to the Burp Suite instead , here `Burp Suite` is a `proxy server`  ✔ 
			- Why this will happen - cuz we gave a port of that localhost ✔ 
			- so firstly request will go from Client to that Burp Suite proxy server then we'll intercept the request & after intercepting the request , if u as a hacker want to forward to the server then only request will go the server ⭐
			- then the server's response came to the burpSuite Proxy server then client ✔
			- so this is MITM attack , Role of the proxy server is to intercept each request & responses also ⭐
		- right now , in Proxy tab > Intercept > intercept is off , but if you keep it off then still we'll get that URL in `HTTP history` but on the intercept by clicking on `Intercept is on` button
		- STEP 6 : on firefox > write `testphp.vulnweb.com` & hit enter
			- once you hit the request then that GET request intercept by burp suite
		- STEP 7 : in burp Suite > Proxy tab > Intercept tab 
			- if we click on `forward` button then GET request goes to the server
		- STEP 8 : now , response will come 
			- go Proxy tab > HTTP history
			- & then double click on that URL , u'll get the response like this ![[WAPT-lecture-6-5.jpg]]
			- so as a response as `200 OK` , we got a HTML code which u can render the page there only - click on `render` button
	- *intercepting via BurpSuite (setting up SSL Certificate issue with https)*
		- `testphp.vulnweb.com` - is a http website 
		- we'll get issues with HTTPS when we intercept coz each `HTTPS` website need SSL certificate ✔
		- Eg : in firefox > write https://demo.testfire.net then we'll get error ![[WAPT-lecture-6-6.jpg]]
		- to avoid/skip this warning
		- *installing SSL certificate*
			- we're running a proxy server on `127.0.0.1:8080` 
			- STEP 1 : so go that browser only which u have done the configuration for localhost & then write http://burp & hit enter
			- now u'll get the page of burp suite ![[WAPT-lecture-6-7.jpg]]
				- this page gives CA (certification authority) , it gives the certificate
			- STEP 2 : click `CA Certificate` button & download it
			- STEP 3 : in firefox > settings > references > search - certificate
			- STEP 4 : click `view certificate` button > import > open it
			- STEP 5 : check both the checkboxes > click ok > then ok , now CA certificate is configured in that browser
			- STEP 6 : in burp Suite > Proxy tab > Intercept tab > turn off the `intercept`button
			- STEP 7 : reload that page again , so u'll not get the error again & that's HTTPS website
		- *role/purpose of SSL certificate in HTTPS* ⭐
			- each HTTPs website needs a SSL certificate , so that website/webapp send the request/data to the web server , that data/request will be in encrypted ✔
			- Eg : ![[WAPT-lecture-6-8.jpg]]
				- u'll get verified by : PortSwigger cuz on firefox , we installed the SSL certificate of PortSwigger ✔
				- means each HTTPS website will get intercept by BurpSuite & no error will come cuz SSL certificate installed on this browser ✔
	- u can skip all these last 2 step , if u use `Open Browser` feature of burp Suite
	- so last 2 steps done if u're using old version of burp suite which hasn't have `Open browser` button burp Suite feature
	- we have `foxyProxy` firefox extension - which u can use if you don't wanna do that like going on settings > preference > & then searching `proxy`  & setup the localhost for the burp Suite proxy browser like this ![[WAPT-lecture-6-9.jpg]]
		- click on Option , u can add Proxy server & see Anuj Sir already setup a Burp Proxy server as `127.0.0.1` like this ![[WAPT-lecture-6-10.jpg]]
		- the movement he want to use Burp proxy , he'll click on that Burp & if he wants to off the proxy , we'll click on `Turn Off (user firefox settings)`

